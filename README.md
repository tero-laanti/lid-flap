# Lid Flap

A Flappy Bird-style game where your MacBook's **lid angle is the joystick**. Open the lid wider to climb and tilt it closed to dive.

**Play:** https://tero-laanti.github.io/lid-flap/

## Requirements
- A MacBook with a lid angle sensor (most MacBook Pro 2019+ and many Apple silicon models; some M1 machines don't expose it)
- Chrome or Edge (uses [WebHID](https://developer.mozilla.org/en-US/docs/Web/API/WebHID_API))

## How to play
1. Press **Space** to connect the lid sensor, then pick the Apple sensor device in the browser prompt. No sensor? Press **K** to use the ↑/↓ keys.
2. Tilt to your lowest comfortable angle and press **Space** to set the bottom.
3. Open to your highest angle and press **Space** to set the top.
4. Test it by flying into both the TOP and BOTTOM zones, then press **Space** to start.

There's no mouse control at all. Other keys:
- **1 / 2 / 3** switch the response mode: Direct (no smoothing), Snappy or Smooth.
- **C** recalibrates from the test screen or the game-over screen.

The corner shows the sensor's live update rate, which is the real limit on how responsive the game can feel.

## How it works
The lid sensor is an Apple Sensor Hub HID device (`VID 0x05AC`, `PID 0x8104`, usage page `0x20`, usage `0x8A`). The game polls feature report 1, which holds the angle in degrees as a 16-bit little-endian value. Everything is in one `index.html` with no dependencies.
