---
title: "Constant lockups/freezing"
date: 2011-03-25
forum: General Help
---

### Post by fallenshadow on 2011-03-25
I noticed in the last month or so that Ubuntu keeps on randomly locking up and freezing.

Most of the time Crtl+Alt+Backspace (zap X) does not work and I have to power down my PC manually.

What has happened good old reliable Ubuntu? :confused:

Its starting to p.i.ss me off now but luckily I haven't lost anything of value as a result of these lockups.

Im running Ubuntu 10.10, any suggestions?

---

### Post by fallenshadow on 2011-03-25
bump!

---

### Post by CVGH on 2011-03-25
Same here on a USB install. I assume it's a Compiz issue, so I've tried disabling as much of it as I can using CCSM...

---

### Post by Cheesehead on 2011-03-25
Well, what do your logs say?

Note the time of a freeze. After a reboot, check the following logs for information around that time.
```

/var/log/dmesg.0
/var/log/syslog
/var/log/messages
/var/log/Xorg.0.log

```

If you find something, post it here.

---

### Post by rgb1701 on 2011-03-25
You could have bad RAM, or overheating RAM, CPU or mobo.

Run memtest+ on you machine overnight.

[http://www.memtest.org/](http://www.memtest.org/)

Download the ISO (burn to CD) or USB stick image and boot from it.

Also, run a RAM only distro for a day or two and see if you have lockups.  Try Lucid Puppy, since it's based on Ubuntu.  Also Parted Magic.

[http://puppylinuxnews.org/releases/lucid-puppy-52-is-released/](http://puppylinuxnews.org/releases/lucid-puppy-52-is-released/)

[http://partedmagic.com/doku.php?id=start](http://partedmagic.com/doku.php?id=start)

You need to rule out all hardware causes before pursuing software issues.

---

### Post by fallenshadow on 2011-03-25
Nope I could find anything abnormal but thats probably because I think it stops recording logs when it freezes.

---

### Post by Cheesehead on 2011-03-25
Since your system hasn't told you the problem in a log, it's time to follow rgb1701's advice next.

---

### Post by CVGH on 2011-03-27
I had another crash as I was switching desktops.
Only thing I saw of note was from syslog.


Syslog:
```
Mar 27 17:55:00 ubuntu kernel: [  278.865536] EXT2-fs (sdb2): error: ext2_free_blocks: bit already cleared for block 958580
Mar 27 17:55:00 ubuntu kernel: [  278.867780] EXT2-fs (sdb2): error: ext2_free_blocks: bit already cleared for block 958581
Mar 27 17:55:00 ubuntu kernel: [  278.870034] EXT2-fs (sdb2): error: ext2_free_blocks: bit already cleared for block 958582
Mar 27 17:55:00 ubuntu kernel: [  278.873786] EXT2-fs (sdb2): error: ext2_free_blocks: bit already cleared for block 958583
Mar 27 17:55:00 ubuntu kernel: [  278.877661] EXT2-fs (sdb2): error: ext2_free_blocks: bit already cleared for block 958596
Mar 27 17:55:00 ubuntu kernel: [  278.879917] EXT2-fs (sdb2): error: ext2_free_blocks: bit already cleared for block 958597
```This is a USB install and sbd2 is a 14GB partition.
GParted says it is unable to find a mount point.
mount:
```
   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1         858      878576    c  W95 FAT32 (LBA)
/dev/sdb2             859       15320    14809088   83  Linux
root@ubuntu:/home/ubuntu# mount
aufs on / type aufs (rw)
none on /proc type proc (rw,noexec,nosuid,nodev)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
none on /dev type devtmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
/dev/sdb1 on /cdrom type vfat (rw,relatime,fmask=0022,dmask=0022,codepage=cp437,iocharset=iso8859-1,shortname=mixed,errors=remount-ro)
/dev/loop0 on /rofs type squashfs (ro,noatime)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/ubuntu/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=ubuntu)
```e2fsprogs is installed according to the software center.
Should I run the disc utility provided in Administration?
I guess it's a fsck GUI?

Thanks!

---

### Post by Alan.Brown on 2011-03-28
I am using a brand new  HP-200-5220a computer and have been having freezing in both Ubuntu 10:10 AND Linux Mint 10 AND openSuSE 10.3 for a couple of months!!   The freezing does NOT occur under Windows 7 on the same machine.  All the above are installed on the hard disk - not run from live DVDs.

I have run memtest several times without any errors.   None of the system logs show any error (understandable because the freezing may block any error message from being logged).   CPU temperature is usually between 30 and 33 C.

I have tried several forums and noticed that this is a very common problem on many different makes and models of computer.   This would suggest that the problem is not hardware related.

Since three distros have been involved I assume that it is a bug in Linux and that (maybe!!) it will disappear in time hopefully with the next version.

When the system freezes there is only one thing that will work - Alt+SysRq+B - **in that order** - this will reboot the computer.

I have not been able to get any help on this matter over the past two months.

Any more suggestions??   Any help??

TIA

Alan

---

### Post by fallenshadow on 2011-04-07
I just did a MemTest today... it didn't find anything wrong!

Im sure the problem is with X as it freezes when I try doing anything slightly intensive. (like playing a fast paced game in a SNES emulator or playing a video file/DVD or playing other 2d games)

Then again it could be the kernel locking up too, im not sure which is the culprit. :confused:

---

### Post by CVGH on 2011-04-07
For me the trouble seemed to be Compiz. Reinstalled to USB but did not install CCSM and so far no hangs...

---

### Post by Dutch70 on 2011-04-07
> **Alan.Brown said:**
> 
When the system freezes there is only one thing that will work - Alt+SysRq+B - **in that order** - this will reboot the computer.

Alan
Hi Alan
The correct way to safely reboot is to hold (Alt+SysRq) and then press...
R-E-I-S-U-B, if you're just going to hit the B, you might as well hit the power button.
[[COLOR="RoyalBlue"]http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/[/COLOR]]("http://fosswire.com/post/2007/09/fix-a-frozen-system-with-the-magic-sysrq-keys/")

Also, post #22 by Nico666 of the link in my sig has worked for me, as well as other people I've given it to with different graphics cards. It doesn't work for everyone. I use this workaround on Ubuntu, Mint, PCLinuxOS, Fedora, Zorin OS and Kubuntu. That's why it's in my sig.

Good luck to all who try it.
Dutch

---

### Post by zarthon on 2011-04-07
fallenshadow: Are you over clocked? Have you tried reseting the BIOS settings to stable/automatic ? 

Have you checked to see if their are BIOS updates for your mother board?

I had freezing problems and a BIOS upgrade fixed the problem.

The problem was not caused by the kernel but i think  a kernel update may have raise the likelihood of the BIOS problem causing a freeze.

---

### Post by nerdy_kid on 2011-04-08
I have a Intel D101 motherboard and the newest maverick kernel causes random hard lockups -- seems to be triggered by watching videos or other graphically related activities.  The 2.6.35-27-generic kernel seems to be much less accident prone.

---

### Post by fallenshadow on 2011-04-08
Nope my processor isn't over clocked and I can't seem to find any BIOS update.

I don't have a working graphics card, so I don't use compiz and therefore compiz could not be a problem here.

> The 2.6.35-27-generic kernel seems to be much less accident prone. 

So should I install a new kernel or what do ye guys/gals think?

---

### Post by Dutch70 on 2011-04-08
So, what do you get when you run this command in a terminal?
```
lspci | grep VGA
```

Also, I don't see how it would hurt to try installing a new kernel, as long as you don't remove the other one, but I'm not a pro in this area...or any area for that matter. :P

---

### Post by fallenshadow on 2011-04-08
Here is what I get:

02:00.0 VGA compatible controller: nVidia Corporation G92 [GeForce 9800 GT] (rev a2)

Thats my graphics card but im not using the official driver for it.

---

### Post by Dutch70 on 2011-04-08
Ok, since you're not using compiz, you won't mind removing it. 
Even if it's not causing your problems. If you're not using it, no sense in having it, is there?
```
sudo apt-get remove compiz compiz-core
```

---

### Post by fallenshadow on 2011-04-09
Ok removed but I don't see how this will affect anything, since I wasn't using it in the first place. :P

---

### Post by owenll on 2011-04-09
My computer was freezing constantly and (seemingly) randomly for a few months - tried everything but no luck. The tip to disable irqbalance here solved this for me - no lockups or freezing for about 4 months now.

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720/comments/6](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720/comments/6)

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/528720)

---

### Post by Dutch70 on 2011-04-09
> **fallenshadow said:**
> Ok removed but I don't see how this will affect anything, since I wasn't using it in the first place. :P

Just to totally rule out the possibility.

I had the same problem as you, but an Intel graphics card that I wasn't using any official drivers on, but it was still causing my freezing problems. Which I thought I was never going to get resolved for a while.

It could be almost anything causing your freezing problem, the more you totally rule out, the closer you'll be to solving it.

Maybe owenll is on to something there. Anything that worked for someone else, is a good place to look.

Best regards

---

### Post by nerdy_kid on 2011-04-11
just a note, I am not using compiz either on the desktop that locks up on me.  The kernel I mentioned fixes the lockups for me.

---

### Post by Dutch70 on 2011-04-11
> **nerdy_kid said:**
> just a note, I am not using compiz either on the desktop that locks up on me.  The kernel I mentioned fixes the lockups for me.

Yeah I think that happens often too. Just depends on what is causing the lock ups.

---

### Post by '76 on 2011-04-12
This has started happening to me recently too, it usually happens 3 times about 5 minutes after start.

Once I reboot and it happens again, it happens a total of 3 times and seems to stop after that.

So it doesn't seem like a heat issue.

It happens on karmic, lucid, maverick ,and natty.

Sometimes it just freezes sometimes X dies and reverts to a terminal with kernel panics.

lets see if we have anything in common, USB both 32 and 64 install, core i7 not overclocked, Radeon card, ocz ssd, usb wifi, g.skill memory.

:confused:

I have removed compiz and irqbalance and it seems to be going well so far.

---

### Post by Rebelli0us on 2011-04-12
Both of my Ubuntu machines are freezing every couple of days...but Windows will run for weeks without rebooting.

Does Linux send back crash reports?

---

### Post by '76 on 2011-04-14
running with cover off of case and fans turned upto 100%.

still freezing 3 times after first boot in the morning after removal of irqbalance and compiz...

Ran memtest all OK, now testing each dimm on its own.

---

### Post by fallenshadow on 2011-04-28
Issue solved by upgrading to version 11.04! :)

---

### Post by '76 on 2011-07-25
I solved my freezing problem by reseating the processor.

I had put off reseating and changing the thermal grease because I have a little Lian-Li case and everything is so tight, its like when you open it its a jack-in-the-box...hard to stuff it all back in...

---

