---
title: "Disable Laptop accelerometer?"
date: 2012-06-14
forum: General Help
---

### Post by shunoob on 2012-06-14
I have an HP Pavilion DV5-1253c, which has a built in accelerometer for its HP 3D Driveguard function. I don't use this at all, and it hasn't given me any issues at all until I tried to use a gamepad(specifically my Dualshock 3) as a game controller.

While setting up the keys on PCSX, I've noticed that while setting up keys, they are all set on the same value every time. Originally, I thought this was an issue with the sensitivity of the Sixaxis accelerometer, but after having played around with some configurations I figured out that the gamepad had nothing to do with those values, it was the accelerometer built into my laptop, which Linux automatically sets up as the default joystick device.

I've looked up on the internet whether others have had the same issue, and there are plenty others who've had the same thing occurring. Some have suggested merely deleting /dev/input/js0, but this doesn't solve the issue so much as dodge it, as it is automatically generated on boot so the accelerometer is registered as a joystick everytime I reboot. I've also found out that the HP 3D Driveguard system(most probably) doesn't work on Linux.

My question is if I could disable the accelerometer as an input device? An even better solution would be for Ubuntu not to register the accelerometer as a joystick. It is very difficult to keep the laptop absolutely level, and since I have back problems my physiotherapist has suggested I use a laptop stand to elevate the laptop up to face level, this elevation causes one axis to always be higher than 0.

---

