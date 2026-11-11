# RallyControl

Motorcycle handlebar BLE controller.

Current version: **1.0.8** (build **9**).

## Modes

The controller has three modes. To change mode, hold the **Mode** button for 1 second and release it.

### TerraPirata

| Button | Action |
|---|---|
| Previous | Previous roadbook item |
| Next | Next roadbook item |
| ODO+ short | ODO+ |
| ODO+ long 1 s | Partial reset |
| ODO− short | ODO− |
| ODO− long 1 s | Lock/unlock |
| Mode short | Partial reset |

### Navigation

| Button | Action |
|---|---|
| Previous | Zoom in (`+`) |
| Next | Zoom out (`-`) |
| ODO+ short | Recenter (`c`) |
| ODO− short | Orientation (`d`) |
| Mode short | Show/hide navigation view (`n`) |

For OSMAnd, enable the external keyboard in:

```text
Settings -> Profile -> General -> Other -> External input devices -> Keyboard
```

### Music

| Button | Action |
|---|---|
| Previous | Previous track |
| Next | Next track |
| ODO+ short | Volume down |
| ODO+ long 1 s | Mute |
| ODO− short | Volume up |
| Mode short | Play/pause |

### Global gestures

| Gesture | Action |
|---|---|
| Mode 1 s and release | Change mode |
| Mode 3 s | Full reset. Does not change mode. |
| Next + Mode 3 s | Enter OTA mode |

Full reset is only sent when Bluetooth is connected.

## LED

| State | Pattern |
|---|---|
| Not connected | Slow blink, 500 ms on / 500 ms off |
| TerraPirata mode | 1 blink of 250 ms, then steady |
| Navigation mode | 2 blinks of 250 ms, then steady |
| Music mode | 3 blinks of 250 ms, then steady |
| OTA started | 5 fast blinks of 100 ms, then steady |
| OTA downloading | Steady |
| OTA up to date / successful | 3 slow blinks of 200 ms, then steady |
| OTA error | Continuous fast blink of 100 ms |

## OTA update

1. Turn on the controller.
2. Hold **Next + Mode** for 3 seconds.
3. The LED blinks 5 times quickly and stays steady.
4. The controller tries to connect to the saved WiFi network.
5. If a new version is available, it downloads and restarts.

WiFi:

- If the saved WiFi network is available, it connects to it.
- Otherwise it creates:
  - SSID: `RallyControl-OTA`
  - Password: `rallyota`
  - Portal: `192.168.4.1`
  - Timeout: 180 s

If the controller says it is already up to date after publishing an update, wait a few minutes and try again.

## iPhone

iOS hides the on-screen keyboard when a Bluetooth keyboard is connected.

On iOS 26+, it can be forced with:

```text
Settings -> Accessibility -> Touch -> AssistiveTouch -> Pointer Devices -> Show Onscreen Keyboard
```

If that option is not available, disconnect the controller to type.
