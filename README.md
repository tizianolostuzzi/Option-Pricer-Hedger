# BSM Option Pricer & Dynamic Hedging Engine

A dependency-free Black-Scholes-Merton option pricing engine written in Python.

## Description

The engine prices European call and put options and computes their risk sensitivities without relying on any statistical library. The Normal CDF is implemented from scratch using the Abramowitz & Stegun polynomial approximation, replacing `scipy.stats.norm` entirely.

Greeks are computed numerically via finite differences — each input is bumped by a small `h` and the option is re-priced, so no closed-form derivative formulas are used. This gives Delta, Gamma, Vega, Theta and Rho directly from the pricer itself.

Market parameters can be entered manually or pulled live from `yfinance` for any real ticker, including spot price, risk-free rate (13-week T-bill), dividend yield and 60-day realised volatility.

The Greek surfaces are plotted interactively in 3D using Plotly, across a grid of spot prices and days to expiry, and exported as HTML files.

For real underlyings, a hedge simulator replays a Delta or Delta-Gamma strategy day by day on historical price data, tracking positions, cash flows and MTM P&L with a full daily ledger.

## Dependencies

```
numpy  pandas  yfinance  plotly  matplotlib
```
