---
title: "Gamepad/Keypad"
date: 2012-05-03
forum: General Help
---

### Post by mindovermaster on 2012-05-03
I don't know where this would go, so I'll just post it here.

I am running Ubuntu 12.0.4

I need either a gamepad or separate keypad to play Minecraft. And I need the buttons able to be emulated. 

I currently have a Logitech Gamepad F310. When i plug it in, Ubuntu doesn't even detected. I did a lsusb, wasn't listed.

I tried the jstest-gtk, but it brings up a blank window.

I couldn't get qjoypad to work, either.

I read around, and no one seems to have hard evidence. And the guides are old, programs no longer in the repositories.

So hardware and/or software. How can I get this to work?

---

### Post by Grumbel on 2012-05-04
> **mindovermaster said:**
> I currently have a Logitech Gamepad F310. When i plug it in, Ubuntu doesn't even detected. I did a lsusb, wasn't listed.
Have you tested the gamepad on Windows? Does it work there? As this sounds more like a hardware issue then a software one, as even unsupported USB hardware should show up in lsusb. Also what output do you get from 'dmesg' when you plugin in gamepad? And have you tried using different USB ports?

---

### Post by mindovermaster on 2012-05-04
It works fine in Windows. Tried the rear and front USB ports.

dmesg shows a whole mess of stuff. From what I can make out of it

```
USB HID v1.11 Joystick [Logitech Logitech Dual Action]
```

So, it sees it, just doesn't know how to utilize it.

Edit: I did read that the XBOX or XBOX360 (wireless or not) controller works pretty good in Linux, using xboxdrv

---

### Post by mindovermaster on 2012-05-04
I think I figured part of it out. On the back of the gamepad there is a  switch for X or D. I had it on D. Switched it to X. Then jtest-gtk saw  it. 

Now, how do i map the buttons? pressing them does nothing. I tried  reyjoystick and joy2key. rejoystick works, looks good on paper, but it  doesn't implement it. joy2key just gave me a "Must specify a target!"

---

