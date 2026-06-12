---
title: "Inconsistent wake from hibernate after dual boot"
date: 2012-02-14
forum: General Help
---

### Post by sparhawkthesecond on 2012-02-14
Hi,

I'm running Ubuntu 11.10 and Windows 7 in a dual boot environment. I can hibernate either OS, reboot the computer, then select the other in the grub menu. Usually they restore fine, but about 20% of the time, Ubuntu dumps me into the log-in screen instead of my normal user screen. There is no arrow next to my username (so I mustn't be logged in), and when I log in, all my windows have gone.

I'm not sure if it's important, but I've set my main account to automatically log in, and also removed the lock screen on wake using ```
$ gsettings set org.gnome.desktop.lockdown disable-lock-screen 'true'
```
I'm unsure how to troubleshoot this, and I've attempted to search the forums, but cannot really find anything. Any help would be much appreciated. Cheers.

---

### Post by sparhawkthesecond on 2012-03-11
The good news is that this problem has not occurred the last 20 or so times I've woken up. However, I seem to be encountering a worse (different?) problem. About half the time, when I attempt to wake from a hibernate (after being in Windows), or even just a suspend, I get a crash. I either get a blank screen, sometimes with a blinking text cursor in the upper left, or a console-like screen of text, with a mouse cursor that's frozen. Once, I even got back into my Ubuntu session, but could not access the hard drive (either through nautilus or terminal).

I'm new to Linux, so I'm not sure what to do. Presumably there are log files somewhere that I can post? Any help is much appreciated.

Cheers.

---

