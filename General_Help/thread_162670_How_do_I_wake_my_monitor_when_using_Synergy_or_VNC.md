---
title: "How do I wake my monitor when using Synergy or VNC?"
date: 2006-04-19
forum: General Help
---

### Post by Scuzuliak on 2006-04-19
Well, I just switched from Fedora Core to Ubuntu and got everything working exactly how I want it to... except one thing.

My Windows PC is running Synergy as a server and my Ubuntu box is a Synergy client. I have power management enabled so my LCD will go to standby. However, when I move my mouse over to my Ubuntu screen, it does not wake up the LCD so I have to do a "xset dpms force on" via SSH (unless I know a terminal is up and type it out blindly). I noticed that when I use VNC to connect in, it also doesn't wake the monitor. I don't really care if VNC wakes the monitor or not, but I assume it's not waking the monitor for the same reason Synergy isn't. When my mouse and keyboard are directly attached to my Ubuntu box, moving the mouse does wake the monitor.

Is there a way get my monitor to wake on mouse movement when there's no mouse physically attached to the computer? This did work in Fedora, so I'm thinking there has to be a way (I'm not knocking Ubuntu, btw... I had lots of issues with Fedora which is why I switched). I am using the latest version of Synergy (1.3.1) and VNC (4.1.1) on both computers.

Thanks in advance.

---

### Post by airtonix on 2006-04-25
can you point us to some steps for installing the synergy client.....im stuck at the stage where you need to install libstdc++-libc6.2-2.so.3

---

### Post by airtonix on 2006-05-05
dont worrie bro...all is good now...its in the repos and I no longer run the demon beast on my machines anymore, so Im of no use to you other than this: when my screensaver kicks in...al i do is move the mouse onto the remote screen and voila...screen saver dissapears.

---

### Post by cpiper on 2006-05-10
Hi Scuzuliak,

Did you come up with a solution for this?  I'm having the same issue with Synergy on Dapper.  It was working fine for me on Breezy up until I hosed my partitions and had to reinstall :/

Thanks,
CP

---

### Post by chadlongstaff on 2007-07-03
It seems this problem is related to gnome-screensaver, if you switch over to the regular xscreensaver it has the API that synergy is looking for.

A little experimenting shows that as well as the option of running 'xset dpms force on' to wake the remote monitor from energy saving mode, you can also simply kill and restart synergys for the same effect. Saves a little blind typing.

---

### Post by Scuzuliak on 2007-07-04
Awesome! Thanks for replying even though this thread is over a year old. I basically gave up on this and disabled power management for the monitor and was manually turning it on and off. Switching to xscreensaver worked like a charm!

I used this guide to switch: [http://ubuntuforums.org/showthread.php?t=195557](http://ubuntuforums.org/showthread.php?t=195557)

---

