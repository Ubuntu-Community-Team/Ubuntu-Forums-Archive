---
title: "Dual partition help?"
date: 2009-09-21
forum: General Help
---

### Post by [ENGAGE]glitch on 2009-09-21
Good afternoon,

I recovered a PC tower that was in the garage of the house that i'm currently living in right now and i replaced the hard drive but had no way of obtaining an operating system without forking over some money (poor college student). I'm running off of a laptop and which i'm sure everyone knows, mobile operating systems are very different. So i decided to throw ubuntu on there because i've worked with that system before and knew it was open source. Just today I got a Windows XP Pro ISO with serial key and want to either wipe the drive clean and make it solely Windows XP or, if it's possible, to make a dual boot of Ubuntu (being the secondary boot) and then Windows XP (being the primary.) I've tried throwing the burnt disk into the tower and running the windows installer but it doesn't read any partitions are on the disk (even though ubuntu is on there) and i get the "blue screen of death" as it's called. I run chkdsk and it says that there are unrecoverable errors on the disk.

Any suggestions?

Thanks
glitch

---

### Post by JC Cheloven on 2009-09-21
As far as I understand, ubuntu is already installed on "the tower", right? 

Windoze doesn't recognize linux partitions, so no surprise in that the xp install disk doesn't recognize any partiton.

I'd do this:
- Backup your valuable data (if any) from the ubuntu disk or partition. The plan is to discard it.
- Run a live cd session, and use gparted to prepare partitions (the first a ntfs one for xp, then an ext3 for ubuntu, plus some swap)
- Install first xp. Then Ubuntu.

You'll end up with a boot menu with the choice of xp/ubuntu.

---

### Post by [ENGAGE]glitch on 2009-09-21
So when XP is all installed and finished with, i just throw the ubuntu cd in and format a second partition?

---

### Post by JC Cheloven on 2009-09-22
> **'[ENGAGE]glitch said:**
> So when XP is all installed and finished with, i just throw the ubuntu cd in and format a second partition?

In short: 
- Yes, you could do that, it will work.

In some detail: 
- You first prepared the partitions from live cd. I'd recommend erasing the existing ones. Please realize that you already wipped your entire hard disk at this stage. Note: when using gparted, click on "apply changes" after every action you take; this is less prone to errors (all care is scarce when managing partitions).
- Then installed xp, and the installation may (or may not) format again the ntfs partition you prepared (not needed, but no harm in doing it).
- Then you start from live cd again, and install ubuntu in the ext3 (or ext4) partition you prepared. Again, the ext3 partition may (or may not, at your choice) be formatted again. Not needed, but will not harm either.

Hope this makes things clear for you. 
Come back to tell us how was it ;-)

---

### Post by P4man on 2009-09-22
There is no need to wipe ubuntu though. You can use the live cd and gparted to shrink the existing ubuntu partition(s), make one for windows, install windows, then reinstall grub to allow the dual boot. Just make sure the windows partition is the first one (on the left side) windows doesn't like to install anywhere else.

---

### Post by TR14RC3 on 2009-09-22
Maybe this will help.

This is what you do.

1) Save any files you want to keep. Because we are going to dump everything and start from the beginning to make it easiest (your operating systems will take care of the partitioning when you install so don't worry about that).

2) Put xp disc in and restart the compter. If it says press any button to boot from cd then press any button. You may have to set the boot order in the bios to cdrom. There are several ways to do this but if you just change it in the bios, it will do it.( If unsure you can google how to boot from cd)

Let xp fully install and load your drivers if needed.

3) Now put the ubuntu disc in and restart the computer. we want to do the same thing with ubuntu as we did with xp (boot from cd).

Now when the install starts it is going to detect that other operating system (XP).
There is an option to leave that alone and use the rest of the disk or you can specify how much disc space you want to allocate to ubuntu. 

You need to specify how much you want to give to ubuntu so you will still have room to save files in xp. And you can split it evenly if you want. However you want to do it.

It is pretty easy just follow the steps on the screen and ubuntu will finish installing taking care of the partitioning for you once you have specified how much space to give it.

Once it finishes and restarts you should get a black screen with options to select xp or ubuntu.

It will start at the black screen every time and if you don't select an OS within so many seconds it will just start XP.

---

### Post by [ENGAGE]glitch on 2009-09-22
Come on people.....i'm not a complete idiot at this stuff. I'm a computer engineer in college or pete sake. I just asked how to get dual partitions on there with ubuntu being the primary right now. I kinda knew already that i'd lose everything, seeing which there is nothing on there in the first place. Sorry for being blunt. Not having a good day. Thanks for everyones help though!! I'll try these suggestions out here in a few mintues

---

### Post by Darkwing-Duck on 2009-09-22
Partition a section that you want windows to go on. Once you install windows you are going to have to restore GRUB. Here is a good way to restore GRUB once you have windows installed.

[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

Hope this helps you out.

---

### Post by [ENGAGE]glitch on 2009-09-22
Ok.....new problem.....when i put in the old hard drive (that works only sometimes after the computer restarts itself 2 or 3 times) none of the partitions show up when i run the recovery disk. (NOTE): the recovery disk is Windows xp pro and the one installed on the hard drive is windows xp home edition. Is it because of the different editions? Like how it was with the recovery disk not seeing the ubuntu partition?

Any other reasons as to why? (this will all lead up to the original question of dual booting)

---

### Post by [ENGAGE]glitch on 2009-09-24
This might sound dumb, but whom would know how to access gparted? I have worked with ubuntu before but have never worked with the partition itself. I've read online that it's a separate live cd.....anyone know?

---

### Post by peterthinking on 2009-09-24
I use Puppy Linux live cd to do that stuff...pup is so small it can all sit on one stick of ram while you run partition stuff (that is included).
To add gnome partion editor to UBUNTU goto add remove programs and search it.

I'm not sure if you can make a live UBUNTU CD off your hard drive so when you run it live it's on there.

---

### Post by [ENGAGE]glitch on 2009-09-30
Ok.......i deleted the master boot record. I put a new windows recovery disk in and went to see if it would read the disk and NOPE. Even with the master boot record being gone and no partition being on there, it still doesn't read it. What is it i'm doing wrong?

---

