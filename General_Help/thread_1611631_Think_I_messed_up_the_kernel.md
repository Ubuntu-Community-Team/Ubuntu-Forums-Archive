---
title: "Think I messed up the kernel"
date: 2010-11-02
forum: General Help
---

### Post by Knowsnothing on 2010-11-02
Okay... I feel like an idiot cuz I think I know how I messed it up, but now I don't know how to fix it.

Through Synaptic, I installed the linux kernel thinking that it would help me with JACK.  Did that, no problems.  Even rebooted a few times with no problems.

Then, because the battery on my netbook wasn't locked in to place, the computer shuts down.  I turn it back on and it doesn't go the splash screen.  Instead, it ask me for my login info.  Once verified, it doesn't go the desktop.  Instead it stays at the command line.  So, I restart hoping the problem will go away.  But nope, my problems are now much bigger.

Whenever I boot through GRUB (version  1.98xxx), I'm given the choice of Linux 2.6.35-23-generic and Linux 2.6.35-22-generic.  No matter which I choose (including recovery) it goes into BusyBox and initramfs with this error message:

"mount:  mounting /dev on /root/dev failed:  No such file or directory
mount:  mounting /sys on /root/sys failed:  No such file or directory
mount:  mounting /proc on /root/proc failed:  No such file or directory
Target filesystem doesn't have requested /sbin/init
No init found.  Try passing init= bootarg"

I've tried messing with the kernel commands a la [http://ubuntuforums.org/archive/index.php/t-649161.html](http://ubuntuforums.org/archive/index.php/t-649161.html) and [http://ubuntuforums.org/showthread.php?t=1399810](http://ubuntuforums.org/showthread.php?t=1399810)

But none of it seems to work!  Super sucks knowing how this happened but not having a solution.

Please help!  Thanks so much

---

### Post by Knowsnothing on 2010-11-02
Thought I'd let you know I'm running Maverick on an Acer notebook.

This is what it looks like when I try to edit the instructions in GRUB:

"recordfail
insmod part_msdos
insmod ext2
set root='(hd0, msdos7)'
search --no-floppy --fs-uuis --set e8c79b5c-2a6e-4bf8-a19a-8b638283c\6ea
linux /boot/vmlinuz-2.6.35-23-generic root=UUID=e8c79b5c-2a6e-4bf8-a\19a-8b638283c6ea ro   quiet  splash
initrd /boot/initrd.img-2.6.35-23-generic"

Thanks!  Not sure what this stuff means, but it seems like it'd be important somehow

---

### Post by lemi4 on 2010-11-02
[OOT]Intriguing...

I find it ironic, but also somewhat interesting, that you're getting more help at your Google Buzz post than you're getting here in the 'official' Ubuntu forums...

InB4: feel free to ask Knowsnothing where exactly is this "Google Buzz post" that I speak of. I ain't no rat :p

*update:* It had been noted (in the fabled "Google Buzz post") that the forums can be a hit-or-miss thing depending on the time that your forum post goes online, but that overall the Ubuntu forums is still a useful resource for getting Ubuntu help.[/OOT]

*update:* The 'infamous' "Google Buzz post" thread has suggested the following particularly useful thread in the forums: **[thread=1244466]mounting /dev on /root/dev failed: No such file or directory[/thread]**

---

### Post by Knowsnothing on 2010-11-02
hahaha.  And which "Google Buzz" "user" from the fabled "Buzz post" might you be?

---

### Post by Knowsnothing on 2010-11-05
Update:  Got it to work, but not using anything I found on the forums.

Instead, using the help of a friend on Google Buzz, I formatted the troubled partitions from Windows and re-installed Ubuntu.  Problem solved.

---

