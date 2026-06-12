---
title: "Wii Mote in Mupen64"
date: 2011-08-15
forum: General Help
---

### Post by Zvlwab on 2011-08-15
I'd like to use a wii mote + nunchuk as a controller for Mupen64.

This is my config file:
```
# Wiimote
Wiimote.Up = BTN_0
Wiimote.Down = BTN_1
Wiimote.Left = BTN_2
Wiimote.Right = BTN_3
Wiimote.A = BTN_A
Wiimote.B = BTN_B
Wiimote.Minus = BTN_SELECT
Wiimote.Plus = BTN_START
Wiimote.Home = BTN_MODE
Wiimote.1 = BTN_X
Wiimote.2 = BTN_Y

# Nunchuk Buttons
Nunchuk.C = BTN_C
Nunchuk.Z = BTN_Z

# Nunchuk Axes
Nunchuk.Stick.X = ABS_X
Nunchuk.Stick.Y = -ABS_Y
```Everything works fine, except that the nunchuk's stick gives a too low input so that I'm unable to run in several games. I googled it, but I was unable to find any good answers.
Also I tried this:
```

Nunchuk.Stick.X_Scale = 2.0
Nunchuk.Stick.Y_Scale = 3.0
```But it just gives some errors when trying to connect

Could anyone tell me how to fix this?

---

