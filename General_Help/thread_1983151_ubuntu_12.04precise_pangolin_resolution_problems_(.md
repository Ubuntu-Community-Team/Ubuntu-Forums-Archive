---
title: "ubuntu 12.04/precise pangolin resolution problems (too low) - NVIDIA video card"
date: 2012-05-19
forum: General Help
---

### Post by anthalamus on 2012-05-19
Hi all,
Just bought a new computer with an NVIDIA geforce GT 520 and thought I'd try the new ubuntu (Linux 3.2.0-24-generic x86_64)... bad start as the only two resolution available to me are 1024x768 and 800x600... Also it detects my monitor as "Laptop" even though it's a regular monitor

I tried:
- in additional driver: tried both versions of NVIDIA (current and current-updates)
- I tried deactivating both and falling back on Nouveau - same problem but it now says "Monitor" instead of "Laptop"
- installing latest nvidia driver 295.53 - even worse: error message (see PS) and only 800x600 left and now even when i reactivate current i also lost 1024x768

i deleted the /etc/modprobe.d/nvidia-installer-disable-nouveau.conf file created and am now using Nouveau again so i can at least have 1024x768...

Any ideas?
Thanks!

PS:
```

Could not apply the stored configuration for monitors
        none of the selected modes were compatible with the possible modes:
        Trying modes for CRTC 354
        CRTC 354: trying mode 640x480@50Hz with output at 1024x768@50Hz (pass 0)
        CRTC 354: trying mode 320x240@51Hz with output at 1024x768@50Hz (pass 0)
        CRTC 354: trying mode 640x480@50Hz with output at 1024x768@50Hz (pass 1)
        CRTC 354: trying mode 320x240@51Hz with output at 1024x768@50Hz (pass 1)

```

---

### Post by papibe on 2012-05-19
Hi anthalamus.

Could you post the content of this file right after booting with the Nvidia driver?
```
/var/log/Xorg.0.log
```
Please paste it here: [http://paste.ubuntu.com/]("http://paste.ubuntu.com/"), and then post back the link here.

Regards.

---

### Post by anthalamus on 2012-05-26
Hi Papibe,

Thanks for your response and my apologies for the long response time, here is the output of /var/log/Xorg.0.log: [http://paste.ubuntu.com/1008628/](http://paste.ubuntu.com/1008628/), a bit too cryptic for me!

I noticed that it switches me automatically to unity 3d (as opposed to 2d with nouveau)

Hopefully someone can help me figure out what's happening..!

Thanks,
Anthony

---

### Post by papibe on 2012-05-26
Thanks.

The monitor is not given its secrets:
```
[    12.234] (WW) NVIDIA(0): Unable to get display device CRT-1's EDID; cannot compute DPI
[    12.234] (WW) NVIDIA(0):     from CRT-1's EDID.
```
In other words, the card is not able to get the EDID data from the monitor (resolutions supported, timings, etc). It is happening very often these days over an analog connection (VGA cable).

My first suggestion would be to try to use a pure DVI or HDMI cable (not a conversion VGA to DVI). That usually solves the problem.

If that not possible, it may be possible to get the EDID data from Windows (as the manufactures drivers have it to cover these cases), and then put it on a file and hardcoded in Ubuntu.

Take a look at post #4 of this [thread]("http://ubuntuforums.org/showthread.php?t=1857772&highlight=edid"), to see how to get it from Windows. 

Tell us how it goes.
Regards.

---

### Post by anthalamus on 2012-05-26
sadly I don't have a windows machine handy :( (or... for the best..)

one question though: could getting a new monitor solve the problem (would likely come with a new cable as well)? I was considering buying a new one soon...

---

### Post by anthalamus on 2012-06-09
An update, the problem is now solved, although I'm not sure which of the two actions taken did the trick:

- I did buy a new monitor
- I re-activated the Recommended nvidia driver ("NVIDIA X server setting" menu), that may have changed since the last I had tried it

Anyway, all good now :)

PS: thanks for the help Papibe

---

### Post by doobydave on 2012-06-10
Excellent. Yet another nvidia resolution problem marked 'solved' after buying new hardware.

I don't blame you, mind. If your computer cannot drive your monitor, it doesn't matter what the rest of it's capabilities are, you wont be able to use them.

---

