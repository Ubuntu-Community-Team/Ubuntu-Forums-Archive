---
title: "Long Boot Delays with Karmic and Grub2"
date: 2009-11-01
forum: General Help
---

### Post by hal8000 on 2009-11-01
Fresh install of Karmic 9.10, the first impression is a much slower boot,
Its about 30 seconds waiting for grub 2 then about 65 secs to load Karmic.  Hardy booted in just 18 secs.

I have 2 drives and 8 operating systems.
Upon boot, I get
Grub loading

followed by almost 30 secs of hard drive activity, before a grub 2 menu.
Its almost as if grub 2 is running grub-update and finding all grub entries for all partitions.

Loading karmic is also slower and a disappointing 65 seconds. I've installed bootchart and will be removing some startup services shortly.

I have reverted back to grub 1 and control booting from Hardy. Now the grub menu is instantaneous, followed by choice of operating systems.

The grub delays may be something that only those of us with multi boot experience, but I get no boot delay with grub 1.

Does anyone else with multi boot get the grub boot delay?

---

### Post by Manksman on 2009-11-01
Yes, I too have a delay, about 50 seconds. I have 7 installations on 3 IDE drives. I am on the look out for the reason for the delay but a lot of disk trashing seems to be going on. I am sure a reason will become apparent and thereafter a fix. It can not be a deliberate design feature for sure.

---

### Post by DeMus on 2009-11-01
> **Manksman said:**
> Yes, I too have a delay, about 50 seconds. I have 7 installations on 3 IDE drives. I am on the look out for the reason for the delay but a lot of disk trashing seems to be going on. I am sure a reason will become apparent and thereafter a fix. It can not be a deliberate design feature for sure.

There are more threads about this subject and in one of them somebody said it is because Grub is on another drive than the OS you want to boot. Is this true for you as well?
If so, that could be it then.

---

### Post by halfsane on 2009-11-04
Is there a fix coming or a workaround?

---

### Post by GonzalitoUY on 2009-12-08
Just updated to 2.6.31-16, on my desktop, and the delay is unbearable.
Grub2 boot as usual, got a 10 second delay to choose, then when it boot, at first is a blinking cursor for 1-2 minutes, then it boot as usual.
Grub2 is on the same drive as Ubuntu/XP, plus W7 on another drive

---

### Post by SeanBlader on 2009-12-08
> **DeMus said:**
> There are more threads about this subject and in one of them somebody said it is because Grub is on another drive than the OS you want to boot. Is this true for you as well?
If so, that could be it then.

How does Grub know which OS I want to boot in order to enable that delay? I have Karmic on one drive and Windows 7 on the other drive and no matter which one I want to boot there's about a 20 second delay just getting a Grub menu. I figured it was the script trying to figure out what to put in for the OS on the NTFS drive.

But I'd love to get it faster since it's on a very fast workstation.

---

### Post by oldfred on 2009-12-08
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/420933)
Slow boot, multi drives, known issue, move boot to same drive & adjust BIOS
sudo dpkg-reconfigure grub-pc

---

