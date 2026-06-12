---
title: "Too high CPU and GPU-Temperature while running Ubuntu"
date: 2011-10-23
forum: General Help
---

### Post by JohannesJo on 2011-10-23
There is a similar thread open to this topic ([http://ubuntuforums.org/showthread.php?t=1868079](http://ubuntuforums.org/showthread.php?t=1868079)), but it seems like there are some differences, so I'm opening a new thread, as I don't want to use his for my problems.

I have an easynote tj65 (2.1 ghz dual core with Geforce GT240M) running Ubuntu 11.10 and Windows 7 in dual-boot-mode.

While Windows 7 doesn't have any comparable issues, Ubuntu is making my notebook warmer and warmer once the CPU-usage of all processes together gets higher than 50-60 percent, which happens as soon as I do anything more than simple browsing, e.g. starting and running banshee. After starting with no other processes running and (cpu-usage: ~1%) the temperature of both cores is at 61 degrees. 

Once it got to 50 percent cpu usage it rises to around almost 90° for both cores  (gpu rises to the same level according to psensors). Sensors tells me that 98° is the critical temperature for my cpu model and i think around 90 is far too close, especially if I'm not doing anything special. The system crashes pretty quickly once my average cpu usage gets beyond 60%.

It also seems like the fan is not as loud as at system startup as it could be in windows while playing graphic-intensive games for example. 

And yes: I cleaned my fan! And no: I can't change anything in my BIOS regarding the fan or CPU.

I hope you can help me -- like this, it is impossible to use the Ubuntu notebook as a productive system. I've been searching this problem for days now, still haven't found out anything useful.

---

### Post by Gawains Green Knight on 2011-10-23
Does the computer physically feel warm or is it just the sensor? Do you have frequency scaling?

---

### Post by JohannesJo on 2011-10-23
It also feels very warm and usually significantly warmer than it did and does with Win 7 booted. 

I suppose by frequency scaling you mean the CPU? Its activated also for my GPU (considering nvidia x-settings it seems to work) and I installed the CPU frequency scaling indicator to test downscaling (although im not quite sure if the indicator is capable of doing so on its own). Its important to note, that the problem was there before the indicator, but i'm not 100% sure if it was there before installing the nvidia drivers. But still its all the same in unity 2d and even with the gnome-desktop installed. The system even gets warm with almost no active processes.

---

### Post by JohannesJo on 2011-10-24
I finally found a solution: [http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html](http://www.webupd8.org/2011/09/jupiter-applet-finally-available-for.html)
Download and install this and activate battery-saving-mode.

If it was due to this bug: [http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround](http://www.techytalk.info/linux-kernel-2-6-38-2-6-39-power-regression-workaround) 
then this using Jupiter is another workaround for it. It seems like in its natural state, that ubuntu or the 3.0 kernel always run in some kind of maximum performance-mode, at least on some machines.

Like mentioned in the other thread Jupiters Power-Safe-Mode is a good way to keep your CPU temperature low. 

I haven't done excessive testing yet though.

---

