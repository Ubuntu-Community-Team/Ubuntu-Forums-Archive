---
title: "1280x800 resolution vanished from displaysetting options"
date: 2009-09-18
forum: General Help
---

### Post by rhythmiccycle on 2009-09-18
i connect and disconnect my laptop (running ubuntu 9.04) to second monitors, at work many times a day.

everything was working great more or less until today. when after i unpluged the second monitor, and tried to bring my laptop back to normal 1280x800 resolution, and it was not an option in the drop-down anymore.

the problem seem to have started when i closed the laptop, then unpluged the monitor, then later opened the laptop (still with no second monitor) the screen flickered, and when i when back to display settings, the 1280x800 resolution vanished.

how to i make it come back? my screen now has 2 black bars on the sides, its annoying.

---

### Post by rhythmiccycle on 2009-09-18
it fixed it self some how, 

i found this page:
[https://wiki.ubuntu.com/X/Config](https://wiki.ubuntu.com/X/Config)

and i was going to try:

```

$ cvt 1280 800
# 1280x800 59.81 Hz (CVT 1.02MA) hsync: 49.70 kHz; pclk: 83.50 MHz
Modeline "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync

```

then 

```
$ xrandr --newmode "1280x800_60.00"   83.50  1280 1352 1480 1680  800 803 809 831 -hsync +vsync
```

but it fixed it self.

i just wanted to put the website, and the code on the post in case someone else (or myself again) has the same problem.

---

