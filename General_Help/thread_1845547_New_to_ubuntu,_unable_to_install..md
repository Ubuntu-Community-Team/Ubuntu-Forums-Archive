---
title: "New to ubuntu, unable to install."
date: 2011-09-17
forum: General Help
---

### Post by barzach on 2011-09-17
Hi,
I'm new to ubuntu and never used it before.
My computer runs windows xp professional sp3 and I want to completely use to ubuntu.

I've downloaded "ubuntu-11.04-desktop-i386.iso" from ubuntu's website and burned it on a disk.

After burning the disk I chose "Demo and full installation" and installed ubuntu 11.04.

After installation complete, it asked me to restart.

The problem is, that my computer does not recognize ubuntu and refuse to show that it's on my computer. When I open my computer it tells me that only xp is on my computer and it opens it automatically.

I really really want to use ubuntu.
hope you could help me out.

---

### Post by 3rdalbum on 2011-09-17
Where did you install Ubuntu to? What disk?

---

### Post by barzach on 2011-09-17
I have two partitions:
C with 40 GB
and D with 250 GB.

and I installed it on D
(Which I now can't even see though My Computer on xp)

---

### Post by barzach on 2011-09-17
Oops I forgot:
The disk is XEROX CD-R 52X (700 MB)

---

### Post by 3rdalbum on 2011-09-17
> **barzach said:**
> I have two partitions:
C with 40 GB
and D with 250 GB.

and I installed it on D
(Which I now can't even see though My Computer on xp)

Are these two different hard disks? Or just different partitions?

I ask because 290 GiB is a very odd size for a hard disk, but 40 GiB and 250 GiB both sound like normal HDD sizes.

---

### Post by barzach on 2011-09-17
Yes, I have 2 Hard Disks.

---

### Post by 3rdalbum on 2011-09-17
Okay. Well, it looks like Ubuntu is installed on the bigger hard disk. XP can't read it, which is normal - XP can't read Linux filesystems.

However, your BIOS is set up to boot from the smaller hard disk that contains XP. If you change the "boot order" or "boot priority" in your BIOS to the bigger disk, you'll be able to boot up both Ubuntu AND Windows. The menu that allows you to boot both operating systems is sitting on your bigger hard disk.

Do you know how to change the boot priority? Usually when you start up your computer you'll see a screen that has the manufacturer's logo, and some words at the bottom such as "Press Esc to enter Setup" or "F12 - Boot Order". Use this to change the boot order to that bigger hard disk. I can't be more specific with this, sorry - every computer does it a little differently.

---

### Post by barzach on 2011-09-17
Thank you very much.
After you told me to change my priority order I restarted
and opened my BIOS, and changed the order.

After rebooting again it worked like a charm (:
Thank you very much for your help,
I wouldn't guessed that this was the problem :D

---

### Post by 3rdalbum on 2011-09-17
> **barzach said:**
> Thank you very much.
After you told me to change my priority order I restarted
and opened my BIOS, and changed the order.

After rebooting again it worked like a charm (:
Thank you very much for your help,
I wouldn't guessed that this was the problem :D

I'm glad I was online at the same time as you, and was able to help.

Since your problem is solved, please mark it as "Solved" - near the top of the page there's a link called "Thread Tools". Click on this and then click the Mark as Solved item. Thanks!

---

### Post by bapoumba on 2011-09-17
> **3rdalbum said:**
> 
Since your problem is solved, please mark it as "Solved" - near the top of the page there's a link called "Thread Tools". Click on this and then click the Mark as Solved item. Thanks!
Came across this thread by chance, marked as solved :)

---

