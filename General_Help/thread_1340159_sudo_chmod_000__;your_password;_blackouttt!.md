---
title: "sudo chmod 000 / ;your password; blackouttt!"
date: 2009-11-28
forum: General Help
---

### Post by prithvi on 2009-11-28
I have typed this command into the terminal window. I just typed it for experimental purpose, after that everything went blank. How to recover from this situation. Help Me.

---

### Post by fluffman86 on 2009-11-28
First, I would try to boot into recovery mode.  When you computer is booting, hold shift (if you installed Karmic from scratch) or press Esc (if you upgraded from or are still running Jaunty) to get to the Grub boot menu.  Use the arrow keys to select the recovery mode (probably the second option available) and press enter.

If the computer boots properly, you'll get a second menu on a blue screen.  Choose to boot into a root console, and you can reset your permissions properly from there with:

chmod 755 /

But if nothing is readable, then the computer probably won't even boot.  Recover your data with a live CD and reinstall.

---

### Post by lswb on 2009-11-28
> **prithvi said:**
> I have typed this command into the terminal window. I just typed it for experimental purpose, after that everything went blank. How to recover from this situation. Help Me.

select "recovery mode" from the grub menu at boot, then "root shell". Not sure of the exact wording. Execute this command "chmod 755 /" and don't ever do what you did again!

If that does not work, boot from a live CD. You will need to mount your hard drive / directory somewhere else in the live CD environment, or it may be automatically mounted for you, possibly under /mnt/sda1 or something similar. Once you have determined the correct mountpoint for the / used by your istalled system, use the same chmod command specifying that mountpoint.

I realize the above paragraph may be unclear if you are not familiar with the terms used. If you need more help post again.

---

### Post by NoaHall on 2009-11-28
Don't ***ever*** chmod anything outside of your /home/, with the exception of /media/disks.

---

### Post by dasunst3r on 2009-11-28
First off, who advised you to type these commands?  If it's not you and someone else on this forum, he/she ought to be banned.

For future reference, here's how the chmod system works:  The three digits represents owner, group, and others, in that order.  Now, each of these digits are actually groups of three bits that gets toggled on/off for the permissions - 4=Read, 2=Write, 1=Execute.  Sum them up to get the number you're looking for

So, 000 means you deny permission to read, write, or execute to everybody.  On the other hand, 755 means all permissions to owner and read+execute for group and others.

Remember: Experience is a very good teacher, but tuition very expensive.  If you're stuck reformatting, we can help recover your data.

---

### Post by nerdopolis on 2009-11-30
you should be able to mount your disk drive with a live cd, and change the permissions back with sudo chmod 755 /mountpoint/of/your/disk 

No format should be required

---

### Post by dasunst3r on 2009-12-01
> **nerdopolis said:**
> you should be able to mount your disk drive with a live cd, and change the permissions back with sudo chmod 755 /mountpoint/of/your/disk 

No format should be required

Concurred.

---

### Post by prithvi on 2010-03-02
Thank you guys for help

---

