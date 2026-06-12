---
title: "update manager's kernel updates killing system"
date: 2011-03-16
forum: General Help
---

### Post by steaksauce on 2011-03-16
It's taken a lot of work, but I have figured out over the course of many many fresh installs over the past few days that the kernel updates from the update manager in ununtu is breaking my system. This is both for the -22 and -27 updates.

Is anyone else having problems with these and/or is there a fix?

---

### Post by Vi3tHoneyX on 2011-03-16
What version of Ubuntu are you running? Also what kind of computer are you working on?

---

### Post by steaksauce on 2011-03-16
> **Vi3tHoneyX said:**
> What version of Ubuntu are you running? Also what kind of computer are you working on?

10.10 and a dell inspiron 1525
Intel dual core processor/intel chipsets of course.
The computer is a little bit older-from 2008

The error is the same as one commonly gound in Linux From Scratch error take a look at [http://www.linuxfromscratch.org/lfs/faq.html#unable-to-mount-root](http://www.linuxfromscratch.org/lfs/faq.html#unable-to-mount-root)
It also kills init when it tries to boot

---

### Post by Vi3tHoneyX on 2011-03-16
After you update your kernel if you tell GRUB to boot the old kernel again will it work?

---

### Post by steaksauce on 2011-03-16
> **Vi3tHoneyX said:**
> After you update your kernel if you tell GRUB to boot the old kernel again will it work?

When and IF the grub appears after the update (sometimes it does, sometimes it doesn't) both kernels as well as their recovery modes fail.

---

### Post by Vi3tHoneyX on 2011-03-16
I think your system is totally dead then...I'm not sure what method there is to fix it besides reinstalling it. (again :( )

I guess the next time you could try updating everything but the kernel to prove if the kernel is the culprit or not...

---

### Post by steaksauce on 2011-03-16
> **Vi3tHoneyX said:**
> I think your system is totally dead then...I'm not sure what method there is to fix it besides reinstalling it. (again :( )

I guess the next time you could try updating everything but the kernel to prove if the kernel is the culprit or not...

I did. Here's my post before I isolated the problem
[http://ubuntuforums.org/showthread.php?t=1705522](http://ubuntuforums.org/showthread.php?t=1705522)

I suppose when I hit crtl+alt+f9 I updated my system and when I couldn't figure out how to get off the screen I rebooted and I thought that I broke my system that way. I gave up hopes on the issue being resolved and did the fresh install, did all updates before anything, and the system died again.

I then downloaded all the updates except everything involving the kernel (as I'm doing now) and isolated the problem being to the kernel 2.6.36 (I think it's 36 now) -22 and -27 updates.

On some digging on Google, someone suggested a memory problem, and I ran the memtest tool from my live CD and everything passed.

I guess I could go without updating the kernel since the system runs fine without it, but it'd be nice to know why the update won't allow the mounting of the root fs, and causes init to be killed and the kernel panic. I can't report it to launch pad since the system can't even boot so I can do bug reporting.

---

### Post by steaksauce on 2011-03-16
My next question is:
is there a way to setup Updaate Manager to have these files unselected by default or remove them from my update list?

---

### Post by steaksauce on 2011-03-17
> **steaksauce said:**
> My next question is:
is there a way to setup Updaate Manager to have these files unselected by default or remove them from my update list?

Bump

---

### Post by Vi3tHoneyX on 2011-03-17
[Look here]("http://ubuntuforums.org/showthread.php?t=704904")

---

### Post by steaksauce on 2011-03-17
Thanks! Also rigged up the best bug report I could, so as far as what we know is concerned, solved.

---

