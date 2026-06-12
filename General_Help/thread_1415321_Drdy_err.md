---
title: "Drdy err?"
date: 2010-02-24
forum: General Help
---

### Post by Mythic_Commodore on 2010-02-24
Hi everybody. I have a computer running Vista 64-bit and Karmic in dual-boot. The computer has recently refused to load Ubuntu. While Vista works fine, whenever I try to load Ubuntu the computer freezes while at the first "stage" (the glowing white Ubuntu logo with no loading bar) and eventually turns into a blinking prompt. When running recovery mode, I get a repeating message about a "DRDY ERR" which seems to repeat ad infinitum, so I eventually just have to shut down the computer.  Could anyone help me figure out what is wrong with Ubuntu and what I can do to fix it? Here are some basic specs:

Intel Core 2 Duo E4700 @ 2.6 GHz

4 GB RAM

XFX GeForce 9800 GT with 512 MB RAM

500 GB hard drive (three main partitions: Vista, Ubuntu, and Vista Recovery).

Thanks!

 mythic


EDIT: I didn't want to bump the thread, but it's been eight months now and everything is still working perfectly, including the hard drive. I did have a motherboard failure occur three months after the original request for help which was preceded by a succession of BSODs on my Vista system, and a graphics card failure two weeks after that, but my hard drive is still chugging along. Guess the error isn't always indicative of a failing drive. Once again, thanks for all the help.

---

### Post by quixote on 2010-02-25
I've never seen that error before, but I searched using that term and apparently it's associated with hard drive failure....  Not so good.  That's not what it always means, but mostly.

So, 1) use the drive as little as possible.  The more you use a failing drive, the faster it goes.

2) Get as much of your important data onto another drive as you can.

3) Boot with an ubuntu LiveCD (doesn't matter which version, really, but you probably have a Karmic LiveCD).  Do not mount the hard drive.  If a drive icon shows up on the desktop, right click on it and select "unmount".

Open a terminal (Applications > Accessories > Terminal) and type```
sudo fdisk -l       *("l" as in "list")*
```That should show you your three partitions.  Note which one is the ubuntu partition (by its size and the fact that it's ext3 or ext4).  Let's say it's "/dev/sda2".

Just to be sure it's unmounted, type "sudo umount /dev/sda2" (without quotes)

Then (at last :)) go on to try to fix it:```
sudo e2fsck -p /dev/sda2 
```(Remember to substitute your actual ubuntu partition name from the fdisk list.)  If e2fsck returns errors and doesn't complete, copy them to your answer, and we'll try to deal with them.  e2fsck can mark off bad blocks, but if your drive is actually mechanically failing, it won't help for long.  After the bad blocks are marked off, assuming that's the problem, you may need to rebuild the grub bootloader so you can boot something besides Vista, but we'll worry about that later.

---

### Post by Mythic_Commodore on 2010-02-28
Thanks for the reply! Would this also apply to my Windows partition on the same physical drive, or is it just the Ubuntu partition I need to be worried about?

---

### Post by quixote on 2010-02-28
If it really is a failing hard drive, the problems could pop up anywhere, any time, including on your Windows partition.  If it's some ubuntu-specific filesystem corruption, and not your hard drive, then it wouldn't spread outside of ubuntu.  

As I say, first get all the data you care about to another drive, USB, something.

Then, in Windows, you could use some of the system tools (I'm pretty sure scandisk has a physical scan option, but it's been years since I used Windows) to do a low level scan.  If that reports no errors, it's probably just ubuntu.

Then you could run the e2fsck command on the ubuntu partition.

---

### Post by asmoore82 on 2010-02-28
it's a failing hard drive, but obviously the failing sectors are under the ubuntu partition.

get anything you care about off of that drive immediately

---

### Post by Mythic_Commodore on 2010-03-01
Thanks for the replies. I've done some quick searches, and I'm seeing some information, namely [this thread]("http://ubuntuforums.org/showthread.php?t=937872"), that seems to indicate that the problem is, in some cases, fixable - it could be due to some less serious problem than a hardware failure. This makes a little more sense to me, as my hard drive is about a year old. I've backed up and am running some scans on the hard drive now and plan to use the given resources (specifically, my Hardy LiveCD) to try and fix this. I'll be sure to update you all on the results.

---

### Post by quixote on 2010-03-02
Yes, if it's just some bad blocks that developed, e2fsck can mark them off and solve the problem.  If you keep getting more bad blocks appearing, though, that would be likely a hard drive problem, even if it is new.  If bad blocks keep cropping up, get a new HD and just use this one for things that don't matter much.

---

