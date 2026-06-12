---
title: "Machine will not boot after 10.04 upgrade"
date: 2010-04-21
forum: General Help
---

### Post by Calcipher on 2010-04-21
I upgraded from Ubuntu 9.10x64 to 10.04x64 today (figuring I'd get in before the rush tomorrow).  Everything went fine, but on reboot all I got was the following message:
```

[Linux-bzImage, setup=0x3400, size=0x3bef40]
[Initrd, addr=0x3782d000, size=0x7c2a54]
```

Well, I figured out that this was simply a problem with grub, so I booted into a live cd, did the whole chroot trick found here: [https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)
while I was chrooted I also did this:
[http://ubuntuforums.org/archive/index.php/t-422523.html](http://ubuntuforums.org/archive/index.php/t-422523.html)

I rebooted, got past grub, and all I got was a flashing cursor...  To get a better idea of what was going on, I edited the line I was booting in grub ('e' on the line) and removed the "nosplash quite" options.  The machine began to boot and I got the standard stuff that you'd expect to find in kern.log.  The system then mounts my drives and that's it, no more output at all.  If, however, I plug in a USB device I do get the USB plugged in kern.log message, but the machine never boots into Ubuntu.

I'd really like to not reload the machine, it isn't a horrible problem as /home is a separate partition, but I have a lot of stuff I'd hate to have to reinstall.  Does anyone have any ideas on how I might get into my installation?

P.S.  I did try to boot the other kernel image I had installed, same problem.

---

### Post by linden940 on 2010-04-21
dont know why this happened but try to reinstall if you dont have any files on there that you dont wish to keep

---

### Post by Calcipher on 2010-04-21
Grrr, reading comprehension low due to the amount of effort I've put into getting this machine working so I missed that this might not be the best forum for my question.  Mayhap a mod could move this to the "Installation & Upgrades" forum?

---

### Post by Calcipher on 2010-04-21
> **linden940 said:**
> dont know why this happened but try to reinstall if you dont have any files on there that you dont wish to keep

I'll be doing this if I have to, but I have a lot installed to the root partition that I'd like to not have to do again (note: I do have backups, just don't want to do all the things I've already done again).

---

### Post by carl4926 on 2010-04-21
Assuming you have all your software sources in place. Try booting to level 3, then do

```
sudo aptitude update
```

```
sudo aptitude full-upgrade
```

---

### Post by renkinjutsu on 2010-04-21
one thing you can try is boot into the "failsafe" or "recovery" entry in grub

then as root: ```
init 2 #wait till it finishes (brings you into multiuser mode)
init 3 #wait till it finishes (multiuser with networking)
init 4 #probably does nothing
init 5 #hopefully bring up gdm
```

The init sequence above with their descriptions are taken from fedora.. so i'm not sure if it's exactly the same on ubuntu.

Just thought it might be worth a shot, moving through each runlevel one at a time to see if it works (or see where it fails)

---

### Post by Calcipher on 2010-04-21
So, to boot into the various runlevels do I just need to add the run level number to the end of the boot string?

---

### Post by Calcipher on 2010-04-21
Whatever the case might be, it seems to hang after the following:
```

[24.830027] EXT4-fs (sda5): warning: maximal mount count reached, running e2fsck is recommended 
[25.585093] EXT4-fs (sda6): mounted filesystem with ordered data mode

```
Note: sda5 is my / partition, sda6 is /home

---

### Post by renkinjutsu on 2010-04-21
the recovery entry in grub should boot you into runlevel 1

init NUMBER changes your runlevel

when you're booted into runlevel 1, you're automatically root, so you can do that "init 2" stuff i mentioned earlier

.. also, while you're in recovery, it might be a good idea to type ```
touch /forcefsck
```
and reboot to let it scan your disk for corruption/etc

---

### Post by Calcipher on 2010-04-21
The problem is that, even with recovery mode, I never get past the kernel output - no command line at all.  Thanks for the help so far.

---

### Post by renkinjutsu on 2010-04-21
any way you can try to boot into an older kernel? one that you used before the upgrade?

If it's not the kernel, you can try doing a fsck on the disks through a liveCD to get rid of that ominous warning during boot and see what happens.

---

### Post by Calcipher on 2010-04-21
Well, the kernel before the upgrade seems to do the same thing.  
I ran fsck from the livecd and got a couple of "last write times in the future errors" which I fixed.  Now, when I boot, I get the same kernel output sans the "checks exceed" thing.  Still won't boot into anything :-/

---

### Post by Calcipher on 2010-04-22
Well, thanks for the help guys.  I'm going to go to bed and see if anyone has any ideas tomorrow; maybe the updates from today to the RC tomorrow will be enough to jog the thing into working.  I'd feel so much better if I had any idea as to why nothing seems to work..

---

### Post by carl4926 on 2010-04-22
Is there any possibility that / became filled with cached packages during the upgrade?

---

### Post by Calcipher on 2010-04-22
> **carl4926 said:**
> Is there any possibility that / became filled with cached packages during the upgrade?

You mean that it ran out of space or that the stuff in it got overwritten?  In both cases, no seems to be the answer.  I have about 14.4 gigs left on the partition (wow, that seems like way more than it needs...) and I can mount the / partition via the liveCD and the file system seems happy.

---

### Post by carl4926 on 2010-04-22
> You mean that it ran out of spaceThat was a thought I had.
If I were you I would backup you important data now.
And consider a new install.
It's not a good practice to use development on a machine you need for work is has some importance to you.

---

### Post by Calcipher on 2010-04-22
Well, I guess I'm just going to reload - it isn't so bad to do this every so often anyways.  For anyone who runs across this and is curious, this is what I'm going to do:
1. Create a liveCD (actually USB in this case)
2. I'm going to boot into the liveCD
3. Next, I'm going to chroot into my current install and use this ([http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/](http://www.arsgeek.com/2006/09/19/ubuntu-tricks-how-to-generate-a-list-of-installed-packages-and-use-it-to-reinstall-packages/)) trick to make a list of everything I had installed on the old system
4. I'm going to make a backup of my sources.list
5. I'm going to reload my machine (lucky for me /home is its own partition so I won't have to deal with loss of data)
6. Though tedious, I'm going to look through the stuff that the guide above says I have installed and get rid of a lot of it (no reason to unnecessarily clutter a new install)
7. Finally, I'm going to use the above guide to reinstall things that don't come default with Ubuntu.
At that point I should be pretty much back to the way things were.  Good times.

---

