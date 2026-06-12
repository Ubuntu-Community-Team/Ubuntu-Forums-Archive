---
title: "Mouse not recognized at startup?"
date: 2011-01-01
forum: General Help
---

### Post by Chikyuu on 2011-01-01
Hi,

Whenever I start up or restart my computer with Ubuntu, it doesn't recognize my mouse at all, it's totally frozen. It's a logitech USB lazer mouse. I have to duck down under my desk and unplug and replug the mouse, then it works just fine for as long as the computer is running, but if I restart or shutdown, it's not recognized again. Any ideas?

---

### Post by TeoBigusGeekus on 2011-01-01
Have you tried with different usb ports?

---

### Post by Chikyuu on 2011-01-01
Well THAT was a weird change of events.

I have two USB ports in the back of my computer, and in the front is a 4-port USB hub.

I thought my MOUSE was plugged into the back, the one I unplugged and replugged with every startup, come to find out, that was my external hard drive! My mouse was plugged into my front hub the whole time. How does replugging an external make my mouse work? 

Anyway, so I switched, plugging mouse into the back and external into the hub. I rebooted the hard drive, Ubuntu saw it (for the first time, the past couple days I haven't bothered trying to open it) and I got a lot of my old files to open, great! One last reboot to see if it sticks.

... And now I can't boot! I switch back to old config, external plugged in back, mouse into hub, still no boot. Unplug external, and not only does it boot, but now my mouse works with no issue. So **apparently** Ubuntu seems to have some kind of issue with my external, it can't boot or startup properly with it plugged in, but replugging it let's it see my mouse? Now let me see. *Replugs External into back port now that I'm done starting up* ... And Ubuntu just opened my external for me, everything's there.

.... I'm a bit confused. But at least I have pinpointed my problem. For some reason having my external hard drive plugged in prevents my mouse from being seen without the EXTERNAL being replugged, OR my computer doesn't even want to boot.

---

### Post by TeoBigusGeekus on 2011-01-01
My guess: cheapo chinese motherboards.
By a good, POWERED usb hub and plug everything into it.

---

