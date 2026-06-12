---
title: "Display"
date: 2011-06-18
forum: General Help
---

### Post by Vol Vox on 2011-06-18
I'm on a netbook, and so the screen resolution is too small for me to use some programs (specifically StopMotion) because they go off into the bottom of the screen.

My resolution is 1024.

Here is what I tried in the terminal, with the response I got...

user@ubuntu:~$ xrandr --output VGA1 --mode 1024x768
xrandr: cannot find mode 1024x768

I've tried with many screen resolutions, and got the same response.

Any help is much appreciated.

---

### Post by wildmanne39 on 2011-06-18
> **Vol Vox said:**
> I'm on a netbook, and so the screen resolution is too small for me to use some programs (specifically StopMotion) because they go off into the bottom of the screen.

My resolution is 1024.

Here is what I tried in the terminal, with the response I got...

user@ubuntu:~$ xrandr --output VGA1 --mode 1024x768
xrandr: cannot find mode 1024x768

I've tried with many screen resolutions, and got the same response.

Any help is much appreciated.Hi, I am going to give you the link for two guides to help you fix your problem.
[https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected](https://wiki.ubuntu.com/X/Config/Resolution#Setting%20resolution%20changes%20in%20xorg.conf%20--%20resolution%20lower%20than%20expected)
I can not find the second link it was on editing the xorg file.

---

### Post by Vol Vox on 2011-06-19
So, after successfully completing the steps in the "Adding undetected resolutions" section, I tried to add the mode. Here is what happened:

> user@ubuntu:~$ xrandr --addmode LVDS1 "1024x768_60.00"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  150 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  25
  Current serial number in output stream:  26


---

