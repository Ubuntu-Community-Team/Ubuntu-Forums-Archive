---
title: "Motion configuration file..."
date: 2011-03-22
forum: General Help
---

### Post by Victormd on 2011-03-22
I'm trying to setup **motion** in ubuntu 10.10. My webcam is detected and works - however, motion does not adhere to my configuration file, especially here:
> # Threshold for number of changed pixels in an image that
# triggers motion detection (default: 1500)
threshold 2

# Automatically tune the threshold down if possible (default: off)
threshold_tune off

# Noise threshold for the motion detection (default: 32)
noise_level 2

# Automatically tune the noise threshold (default: on)
noise_tune off

I ran motion in setup mode to check the levels I was getting and based on the output, my levels are useless, here's an example:
> [1] Changes:   140 - noise level: 13
[1] Changes:   209 - noise level: 13
[1] Changes:   352 - noise level: 13
[1] Changes:   461 - noise level: 13
[1] Changes:   651 - noise level: 13
[1] Changes:   865 - noise level: 13
[1] Changes:   986 - noise level: 13
[1] Changes:  1065 - noise level: 13
[1] Changes:  1115 - noise level: 13
[1] Changes:  1133 - noise level: 13
[1] Changes:  1220 - noise level: 13
[1] Changes:  1295 - noise level: 13
[1] Changes:  1308 - noise level: 13
and no motion was detected, only when the default (1500) was reached, did motion capture images...

Any thoughts?

---

### Post by Sebastian.Ovide on 2011-04-08
same problem here....

---

### Post by keithandr2 on 2011-07-24
I'm having a similar problem in mint9, it won't save videos only images and it dumps them straight to the home folder instead of creating /tmp/motion like it should

---

### Post by keithandr2 on 2011-07-25
its because your not using motion as root, if you use sudo motion it should work properly, or just give the user root access to the motion folder

---

