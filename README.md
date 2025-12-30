# Mini V-JEPA (Vibe-Coded)

This repository contains a **Mini V-JEPA** implementation created during a vibe-coding session. The primary goal was to learn and internalize the concepts behind the Joint-Embedding Predictive Architecture (JEPA) by building a minimal version from scratch.

## What it does

- Generates synthetic grayscale videos of a **white 3×3 ball on a black background**.
- Trains a model to predict a **future latent representation** from a **context latent representation** (JEPA-style).
- Includes a simple “fail-safe” decoder so latents can be visualized back as pixel frames for verification.

## Training setup

- **Epochs:** 1500
- **Data:** random batches of synthetic videos
- **Video:** ball moves in random directions at random speeds (per-sample variability)
- **Goal:** predictor learns to map context → near-future latent state

## Current results / status

- The **predictor works well for immediate future prediction** (short horizon), capturing the ball's position accurately.
- **Longer-horizon extrapolation shows multimodal uncertainty** (e.g., predicting two possible paths simultaneously). This is likely due to the simplistic nature of the current video generator, which produces ambiguous or inconsistent physics trajectories.

## Notes

This project was built specifically to understand JEPA architecture mechanics (context vs. target encoders, EMA updates, predictor logic) through hands-on coding.

## How to run

1. Install dependencies (`torch`, `numpy`, `matplotlib`).
2. Run the script/notebook.
3. Inspect:
   - `z_context`, `z_target`, `z_pred`, and rollout latents
   - decoded frames for predicted and extrapolated futures

## Ideas for improvement

- Refine the video generator to include consistent physics (e.g., wall bounces, velocity conservation).
- Experiment with longer context windows to reduce trajectory ambiguity.
- Implement an **Action-Conditioned** predictor to steer the latent state explicitly.
