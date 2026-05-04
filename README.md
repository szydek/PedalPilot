# PedalPilot

**A Max for Live device for foot-controlled navigation of Ableton Live Sessions, featuring bounded track selection, gesture-based actions, and adaptable MIDI controller mapping. Originally built with the FBV Express MkII, but compatible with other MIDI foot controllers.**

---

## Overview

PedalPilot is a **Max for Live MIDI device** designed to turn a simple MIDI foot controller into a powerful hands-free Ableton Live Session navigator.

Built around the idea of **temporal gestures** (tap / hold / long hold), PedalPilot allows a limited number of foot switches to perform multiple context-aware actions—without requiring simultaneous pedal presses.

PedalPilot was originally developed for the **Line 6 FBV Express MkII**, but should work with most **momentary MIDI foot controllers** that send MIDI CC messages.

---

## Features

* **Bounded Track Selection**
  Limit navigation to a configurable range of tracks to avoid accidental triggering outside your performance zone.

* **Wrap-around Navigation**
  Moving left from the first track wraps to the last track (and vice versa).

* **Gesture-based Actions**
  Assign multiple actions to a single pedal based on press duration.

* **Session Navigation**
  Navigate tracks, scenes, clips, and transport controls—all by foot.

* **Adaptable MIDI Mapping**
  Configure MIDI CC and Channel assignments directly within the device.

* **Dedicated Control Track Workflow**
  Runs on its own MIDI track for easy routing and consistent behavior.

---

## Controller Setup (Important)

PedalPilot expects a **momentary MIDI foot controller**.

**Your controller must be configured to Momentary mode**
(press = ON, release = OFF)

Latch / Toggle mode will not work correctly for hold gestures.

### Default MIDI Input

By default, PedalPilot listens for:

* **CC# 7**
* **Channel 1**

This was chosen to work out-of-the-box with the **Line 6 FBV Express MkII** expression pedal, but can be changed inside the device.

### Required MIDI Mappings

Only **4 footswitches** need to be mapped:

* **Left / Scene Up**
* **Right / Scene Down**
* **Fire**
* **Delete**

PedalPilot derives additional actions through gesture timing:

* tap
* hold
* long hold

This means a simple 4-button controller can perform many Session navigation tasks without simultaneous pedal presses.

---

## Gesture Timing

Default timing thresholds:

| Gesture     |    Duration |
| ----------- | ----------: |
| Short Press |    0–299 ms |
| Hold        | 300–1499 ms |
| Long Hold   |    1500+ ms |

---

## Default Mapping (FBV Express MkII Example)

| Pedal                | Short Press | Hold        | Long Hold        |
| -------------------- | ----------- | ----------- | ---------------- |
| **A (Fire)**         | Fire Clip   | Start Scene | Toggle Transport |
| **B (Delete)**       | Delete Clip | —           | —                |
| **C (Left / Up)**    | Track Left  | Scene Up    | —                |
| **D (Right / Down)** | Track Right | Scene Down  | —                |

---

## Installation

1. Add `PedalPilot.amxd` to a dedicated MIDI track in Ableton Live

2. Set the track routing:

   * **MIDI From** → your foot controller
   * **Monitor** → `In`
   * **MIDI To** → `No Output`

3. Configure your foot controller for **Momentary mode**

4. MIDI-map the four pedal buttons:

   * Left / Scene Up
   * Right / Scene Down
   * Fire
   * Delete

5. (Optional) Configure:

   * MIDI CC (default: **7**)
   * MIDI Channel (default: **1**)
   * First Track
   * Last Track

---

## Example Set Layout

```text
Audio Tracks      ← controlled tracks
Input Track       ← audio input / source
PedalTrackMIDI    ← dedicated controller track
└── PedalPilot.amxd
```

PedalPilot listens for MIDI input on its dedicated track and performs Session navigation actions within the configured track range.

---

## Configuration

### MIDI

* **CC#** → MIDI controller number (default: **7**)
* **Ch#** → MIDI channel (default: **1**)

### Track Range

* **First** → first controlled track
* **Last** → last controlled track

This creates a **safe control zone** for live performance.

---

## Requirements

* Ableton Live + Max for Live
* MIDI foot controller (must support momentary mode)
* Recommended: **Line 6 FBV Express MkII**

---

## Roadmap / TODO

* [ ] Save / recall pedal mapping presets
* [ ] Custom gesture timing thresholds
* [ ] Repeat-on-hold navigation
* [ ] Optional double-tap gestures
* [ ] Visual feedback for selected track
* [ ] Additional controller templates
* [ ] Example Ableton demo set

---

## Contributing

Ideas, improvements, and alternate controller mappings are welcome.

If you adapt PedalPilot for another MIDI foot controller, please share your setup.

---

## Credits

Created by **Steve Zydek / Wavefiler**


