---
title: "Disabling a USB device/port"
date: 2009-09-02
forum: General Help
---

### Post by Zorael on 2009-09-02
I have a netbook with a card reader integrated into it, that I never ever use, ever. It's connected to the motherboard via USB, and always at the same device "address" 1-6 (or bus 001 device 002, which seems to be the same for some reason).

I'd like to disable it. powertop says it's active 100.0% of the time, and even following its suggestion to enable USB suspend doesn't lower that.

Is there any way to tell the kernel to just, not power this device? I've been looking through **/sys/bus/usb/devices/1-6/** (specifically the **power** subdirectory), but I haven't found something apparent like **state** that I can pipe **0** to.


edit: I think piping "**suspend**" to **/sys/bus/usb/devices/1-6/power/level** did the trick. At least powertop isn't complaining anymore, yay. I just wish I had a card to try it out with.
```
$ echo suspend | sudo tee /sys/bus/usb/devices/1-6/power/level
```

---

### Post by ujodarko on 2009-09-03
Sorry, I don't know how to help you. I only have similar question about disabling power to specific USB port/device.

You see, I have installed 9.04 on external 2.5" HDD that is powered by USB port. Everything works just fine but when shutting down computer, it seems that HDD is suddenly cut of from current before it has been gently and safely switched off. You know... it looks like turning laptop off by presing power switch for couple of second instead of regular precedure by shutdown script (lets say by kernel).

So, how is it possible to make USB device turn off regulary and then turn off power to related USB port. 

Sorry if I made mistakes in english, hope you understood my question.

Thnx.

---

