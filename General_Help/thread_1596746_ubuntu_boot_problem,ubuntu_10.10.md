---
title: "ubuntu boot problem,ubuntu 10.10"
date: 2010-10-14
forum: General Help
---

### Post by reza1717s on 2010-10-14
After starting my computer & select ubuntu to boot,instead of regular ubuntu screen boot option which i could choose between normal boot & recovery mode,i got a new screen :
"GNU GRAB version 1.98*20100004-5ubuntu3
Minimal BASH-like line edition is supported,for the first word,TAB
lists possible command completion , Anywhere else TAB lists possible device or file completions.

grub>_                                                      "
any possible solution or suggestion please ?
I tried : startx & sudu startx , won't recognized these commands.

---

### Post by oogabubchub on 2010-10-23
I'm getting this same exact problem. Any solutions? I've googled the issue and it seems like others have had the problem in the past, but the solutions posted were in relation to grub and not grub2. I'm brand new to Linux and Ubuntu, so I'm not really too familiar with how I would adapt those solutions to grub2 (eg. no 'find' command).

---

### Post by Hippytaff on 2010-10-23
You could try fixing grub2 with

```

sudo update-grub

``````

sudo grub-install /dev/sda

```

forgot to mention booting from a liveCD or liveUSB (or alternatively super grub disc) [www.supergrubdisk.org/index.php](www.supergrubdisk.org/index.php)

---

### Post by oogabubchub on 2010-10-23
> **Hippytaff said:**
> You could try fixing grub2 with

```

sudo update-grub

``````

sudo grub-install /dev/sda

```forgot to mention booting from a liveCD or liveUSB (or alternatively super grub disc) [www.supergrubdisk.org/index.php]("http://www.supergrubdisk.org/index.php")
I'm getting

```
error: unknown command 'sudo'.
```

I don't have any blank CD's, would USB be just as effective?

---

### Post by Hippytaff on 2010-10-23
You can boot from usb - but as far as I know there have on occassion been some issues using a liveUSB with 10.10, so maybe make a 10.04 liveUSB, then try the grub fix above :-)

Forgot to add this link - [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)

---

### Post by oldfred on 2010-10-23
Have you tried manual booting?

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode](https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode)
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd
      boot

Where X is 0 or a if first drive and Y is partition number 1 thru n.
i.e. hd0,1  sda1
or hd0,5 sda5

---

### Post by oogabubchub on 2010-10-23
> **oldfred said:**
> Have you tried manual booting?

[https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode]("https://help.ubuntu.com/community/Grub2#Command%20Line%20&%20Rescue%20Mode")
Express Boot to the Most Recent Kernel
 Command Summary ls to see drive X & partition Y (hdX,Y) or sdXY:
      ls
      set root=(hdX,Y)
      linux /vmlinuz root=/dev/sdXY ro
      initrd /initrd
      boot

Where X is 0 or a if first drive and Y is partition number 1 thru n.
i.e. hd0,1  sda1
or hd0,5 sda5After reading through that link, it seems like my Ubuntu should be at hd0,5 since I'm dual-booting with Win7 (installed originally with wubi). However, when I run "ls" the response is:
```
(memdisk) (loop0) (hd0) (hd0,msdos2) (hd0,msdos1)
```msdos1 seems to be my "System Reserved" which was created when I first installed Win7, and msdos2 is most likely my Win7 partition. It doesn't look like there is a Linux partition if I'm correct.

*Background*
I installed Ubuntu on my Alienware M17x laptop using Wubi downloaded from the Ubuntu website. Had some issues with my nVidia GTX 260m and followed some instructions from this forum to get the latest driver from the nVidia website installed. Everything was working great until I booted up and was told that I was running 10.04 when I thought it would be 10.10 (since that is the version shown on the Ubuntu main page). After upgrading through the Update Manager, I tried to boot up and was greeted with the error the OP posted. Now I can't find the kernel at all.

Should I just try to run Wubi again?

P.S. To clarify, I'm brand new to Linux and all this command line stuff is like Latin to me.

---

### Post by drs305 on 2010-10-23
I have some specific instructions for booting Wubi from the command line in this thread if you would like to try again. (Yeah, it's command line ](*,) )

You should probably start at the top, but the procedures are in the "Wubi Only" section.
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")

---

### Post by oogabubchub on 2010-10-23
> **drs305 said:**
> I have some specific instructions for booting Wubi from the command line in this thread if you would like to try again. (Yeah, it's command line ](*,) )

You should probably start at the top, but the procedures are in the "Wubi Only" section.
[Grub Rescue Prompt Megathread]("http://ubuntuforums.org/showthread.php?t=1594052")Would it not be easier to just log into Win7 and run Wubi from there again? Or would this mess things up because there is potentially still a Ubuntu installation there?

I went into this thinking that fixing these problems would be a great learning experience. It's starting to feel more like a pain when there is probably a much easier solution.

BTW, Thanks for all the help from everyone :D

---

### Post by drs305 on 2010-10-23
> **oogabubchub said:**
> Would it not be easier to just log into Win7 and run Wubi from there again? Or would this mess things up because there is potentially still a Ubuntu installation there?

I went into this thinking that fixing these problems would be a great learning experience. It's starting to feel more like a pain when there is probably a much easier solution.

BTW, Thanks for all the help from everyone :D

It's often easier just reinstalling. I just wanted to give you the option if you wanted to try to access your Wubi install. If you decide to reinstall Wubi, uninstall the current one if possible through the Windows Control Panel, Add/Remove Programs.

---

### Post by ricepw on 2010-10-23
For wubi install , which it looks like you have:use:

set root=(loop0)

then

at grub> type linux /vmlinuz root=/dev/sda5 (or sdc5, if sda5 doesn't work)
                     loop=ubuntu/disks/rootdisk ro

               
                     initrd /initrd.img
                     boot



Let us know.

---

### Post by oogabubchub on 2010-10-24
> **ricepw said:**
> For wubi install , which it looks like you have:use:

set root=(loop0)

then

at grub> type linux /vmlinuz root=/dev/sda5 (or sdc5, if sda5 doesn't work)
                     loop=ubuntu/disks/rootdisk ro

               
                     initrd /initrd.img
                     boot



Let us know.Tried this, and it did the most out of everything else, but I think my computer might have attempted to try to turn the universe upside down:
```
Begin: Mounting root file system ... /init: line 239 **divide by zero**
1.224975 Kernel panic - not syncing: Attempted to kill init!
```Unfortunately, it ended with a blinking white line (no grub>), no allowable input, and blinking scroll lock and caps lock indicators.

---

### Post by oldfred on 2010-10-24
You do not have an sda5.

(hd0,msdos2) (hd0,msdos1)

Says you only have sda1 and sda2. hd0 and MBR based partitions one & two.
So trying sda5 would cause big problems. It depends is you installed wubi in c: which is probably sda1 or D: which then would be sda2.

---

### Post by oogabubchub on 2010-10-24
> **drs305 said:**
> It's often easier just reinstalling. I just wanted to give you the option if you wanted to try to access your Wubi install. If you decide to reinstall Wubi, uninstall the current one if possible through the Windows Control Panel, Add/Remove Programs.I followed these instructions and ran into a problem that I keep having. After installing Ubuntu, I get a blank (black) screen before getting the grub menu. When installing using Wubi, after restarting and choosing OS, it gives a message that installation is completing and counts down to 0. After that it's simply a blank screen and no boot up sound.

I went out to buy a blank CD so I could use a liveCD but it did not solve the problem. After booting with the liveCD, I get a purple screen with two small symbols at the bottom, then it goes straight to a blank screen. I'm unable to get to the command line or do anything.

It seems like the problems are associated with my nVidia GTX 260m, but that is more or less a guess. When I had my first successful install, I'd have success fixing the issue when I added 'nomodeset' from the GRUB menu. Any ideas? Again, thanks for all the help.

---

### Post by oogabubchub on 2010-10-24
Sorry for the double post, but I think I've fixed the issue with the blank screen. My Alienware M17x has an integrated GPU (nVidia GeForce 9400) and a discrete GPU (nVidia Geforce GTX 260m). Normally with Win7 I run it in Hybrid SLI config, but for Ubuntu, I disabled the Hybrid SLI via the BIOS. What I didn't realize was that I also needed to disable the integrated GPU. After disabling that, the liveCD worked just fine.

---

### Post by drs305 on 2010-10-24
> **oogabubchub said:**
> I think I've fixed the issue with the blank screen. My Alienware M17x has an integrated GPU (nVidia GeForce 9400) and a discrete GPU (nVidia Geforce GTX 260m). Normally with Win7 I run it in Hybrid SLI config, but for Ubuntu, I disabled the Hybrid SLI via the BIOS. What I didn't realize was that I also needed to disable the integrated GPU. After disabling that, the liveCD worked just fine.

Oh yeah, that was my next guess.... hehe.

Glad you were able to figure it out - it probably would have taken days/weeks for the rest of us.

So are you having any problems installing now or is everything ok?  If/when everything is working please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

If you are still having problems please restate what they are now.

---

### Post by oogabubchub on 2010-10-24
> **drs305 said:**
> Oh yeah, that was my next guess.... hehe.

Glad you were able to figure it out - it probably would have taken days/weeks for the rest of us.

So are you having any problems installing now or is everything ok?  If/when everything is working please mark the thread SOLVED via the 'Thread Tools' link near the top right of the first post.

If you are still having problems please restate what they are now.

Unfortunately, I came across another error. After installing successfully in Windows 7, I restarted as directed by Wubi. After booting into Ubuntu, it attempted to finish up the install, but before finishing, I received the error: ```
No root file system is defined. Please correct this from the partitioning menu.
```Most of the responses to this error that I've found have talked about setting '/' as your root, but I never partitioned the drive or was given the option to do something like that.   Sidenote: I'm not the original poster, so unfortunately I can't change the topic title. If anything, a mod would have to mark it Solved, or move my posts to a separate thread (sorry for thread hijacking).

---

### Post by oogabubchub on 2010-10-25
Final update: I started from scratch and everything is working perfectly now. Scrapped Wubi and decided to go with a liveCD install on its own partition.

Cliffnotes:
-Defragged
-Shrank Windows 7 partition (freed up 30gb on my 1TB RAID0 config)
-Burned Ubuntu 10.10 liveCD
-Booted and installed from liveCD
    +100mb ext3 partition for GRUB (mounted at /boot)
    +28gb ext4 partition for Ubuntu (mounted at /)
    +2gb swap partition
-Installed drivers
-????
-Profit


Thanks for all the help guys. I know I'm not the OP, but maybe someone could mark this thread as SOLVED since I don't think the OP is coming back to look for it.

---

