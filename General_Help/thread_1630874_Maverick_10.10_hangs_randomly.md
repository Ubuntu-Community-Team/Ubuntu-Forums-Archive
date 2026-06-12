---
title: "Maverick 10.10 hangs randomly"
date: 2010-11-25
forum: General Help
---

### Post by twitty1437 on 2010-11-25
Hi all, i have no clue at all why my system hangs randomly despite trying to install it fresh for a few times. I'm duo booting with XP, when i run in XP, I don't experience any problem at all. 

But in Ubuntu, i can sometimes use it for more than a day with Rhythmbox, Chrome, Openoffice, Evolution running until it hangs. Sometimes it happens just 10-15mins after logging in to Ubuntu. I don't do heavy computing on my pc, i only use those programs mentioned above. When it hangs, i can't do anything but to had reset.

What i have tried:
- changing Bios setting
- Flashed a newer and older version of Bios
- run it Ubuntu failsafe mode and it was perfectly find
- ran memtest and CPU test separately for more than 10 hrs, no problem
- i thought it's a graphic problem, tried X-swat, xorg-edgers, but to no avail
- it hangs on both Kernel 2.6.35-22 and 2.6.35-23

You input is highly appreciated.

Thanks

---

### Post by twitty1437 on 2010-11-26
Any expert out there has any input to this?

---

### Post by sikander3786 on 2010-11-26
Welcome to the forums :-)

First of all, remember that I am no expert. I can however give you some pointers on that.

> run it Ubuntu failsafe mode and it was perfectly find

If it runs fine in failsafe mode, it is definitely a graphics problem.

So which graphics card do you have? And did you install proprietary drivers for that? Try looking under System > Administration > Additional Drivers.

And how much RAM do you have?

Modern X doesn't need xorg.conf any longer but if you generated one yourself, please post the output of

```
cat /etc/X11/xorg.conf
```

---

### Post by twitty1437 on 2010-11-26
thanks for ur reply [sikander3786]("http://ubuntuforums.org/member.php?u=806649"), 
i did not install any proprietary drivers.
i have 1.7G RAM, was running a ATI Radeon 9600SE, i just change my graphic card to another old card: ATI Radeon 9800SE. Will see how it goes and update. 
Will post xorg.conf if it does hang... hopefully not..

By the way, when i run System Monitor > Help > Report a problem, there will always be something under XsessionErrors like:
- polkit-gnome-authentication-agent-1
- nautilus:1451
- nm-applet:1459
- ibus-daemon:1369

are all there critical???

---

### Post by sikander3786 on 2010-11-26
> i did not install any proprietary drivers.

Some times the issue gets sorted by installing those drivers. Look under System > Administration > Additional Drivers and if available, activate the current/recommended drivers.

---

### Post by twitty1437 on 2010-11-27
It's really the Graphic card problem i think.. 2 straight days with no hang... but it's kind of strange that the faulty graphic card ran well in XP

---

### Post by sikander3786 on 2010-11-27
> **twitty1437 said:**
> It's really the Graphic card problem i think.. 2 straight days with no hang... but it's kind of strange that the faulty graphic card ran well in XP
Yes that happened to me too. My faulty Graphics Chipset used to work well under Windows Server but Ubuntu couldn't even boot the GUI at all. It used to boot to the the tty instead. And I guess, Linux is good at recognizing hardware problems ;-)

Glad the issue has been identified for you and sad that your graphics card was faulty :-)

Happy Ubuntu-ing!

---

### Post by Earl_Maroon on 2010-11-29
I think I'm having the same problem, but I'm pretty sure it's an issue with my graphics driver (for ATI legacy) rather than a hardware issue.

---

### Post by sikander3786 on 2010-11-30
> **Earl_Maroon said:**
> I think I'm having the same problem, but I'm pretty sure it's an issue with my graphics driver (for ATI legacy) rather than a hardware issue.
This thread is marked "Solved" so not many people will be looking at it. It'd be better to start a new thread and post your hardware specs/graphics card model and Driver version.

Besides that, you can try reconfiguring your graphics as an initial step and see if that helps.

```
sudo dpkg-reconfigure -phig xserver-xorg
```

Or install the open source drivers as mentioned here.

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Continue your post in the new thread if needed.

Good Luck!

---

