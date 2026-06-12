---
title: "Ctrl + Alt + Backspace"
date: 2006-02-10
forum: General Help
---

### Post by cyberb0b on 2006-02-10
After a normal 5.10 install, I did the updates, then started following the  Unofficial Ubuntu 5.10 (Breezy Badger) Starter Guide, and I got to this part:

[http://easylinux.info/wiki/Ubuntu#How_to_restart_GNOME_without_rebooting_computer]("http://easylinux.info/wiki/Ubuntu#How_to_restart_GNOME_without_rebooting_computer")

To restart X after installing the NVIDIA drivers, I pressed Ctrl + Alt + Backspace and the computer almost instantly turned off.  I pressed the power button to turn it back on and it booted, but that's not supposed to happen.

I don't know if the computer always did that (i.e. when it had windows), but several times since then I've needed to restart X and done it again accidently.  Same thing, instant off.

Is this a bios option?  Anyone else had this happed?

---

### Post by queenorych on 2006-02-10
It shouldn't turn off.  It may kick you into a text shell.  run 'sudu /etc/init.d/gdm restart' to turn the gui back on.

If it is powering off, you probably got a nice hardware problem.  Good luck.

---

### Post by cyberb0b on 2006-02-10
[QUOTE=queenorych]...If it is powering off, you probably got a nice hardware problem.  Good luck.[/QUOTE]

Ouch.  Not what I wanted to hear.  It most definately is powering off.  The first time it happened I just stared at it like a deer in headlights for 5 minutes before I came to accept that it was off.

The computer also booted into 640x480 graphics one day out of the blue with no other options in the menus.  Powered down, powered up, higher resolution options were back.

I hate hardware problems.

---

### Post by annsachd on 2006-02-10
I had the same problem with the suddenly 640x480 appearing. Just ran the setup and was back to normal.

That is odd the computer would shutdown like that.

---

### Post by tukster on 2006-02-17
hm i have almost the same prob, well no but, when i press ctrl-alt-backspace
my screen goes black and nothing happens, all i can do is restart

---

### Post by Mr Green on 2006-03-07
[QUOTE=tukster]hm i have almost the same prob, well no but, when i press ctrl-alt-backspace
my screen goes black and nothing happens, all i can do is restart[/QUOTE]

I'm having the exact same problem. "No signal from monitor" when I try to restart X or logout, and then I have to  ctrl-alt-del to reboot. I think this problem appeared after I installed the ATI drivers as it was working previously.

Any help or suggestions anyone?

---

### Post by justleen on 2006-03-07
i've had the same (X turning black, no shell appeared) when trying to install the ATi drivers.. i just rebooted, CTRL-ALT-F1, and finished the install from there.. (after an apt-get install lynx to go back to the instructions though.. :) )

---

### Post by cyberb0b on 2006-03-13
A quick update, if anyone cares.  The motherboard on this system is an ECS L4S8A2 v1.0 which is a piece of junk, so that might be the problem.  I ran memtest off the dapper flight 5 live CD and it had a bunch of errors, so the memory is bad.

Why is there so much crappy hardware out there?

---

