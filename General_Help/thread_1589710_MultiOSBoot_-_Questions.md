---
title: "MultiOSBoot - Questions"
date: 2010-10-06
forum: General Help
---

### Post by amjjawad on 2010-10-06
Hi there,

I guess this is the right place to post this thread.

First thing first, I'm not an advanced user, I've been with Ubuntu/Linux for few months so easy on me :D
I'm trying to learn as much as possible about Linux and its distribution/versions. I'm reading many threads/articles in no time.
While I was searching/reading, I found this:

[https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)
> 
The method here involves creating a small (approximately 100 Mb) boot partition in which to store the Grub files. These files will be copied from the Grub files that are created during the first Ubuntu Linux OS installation. The initial main Grub menu will be kept in this small boot partition and will be edited so that Grub will then chainload the bootloader files for whichever Windows, (K)ubuntu, or other Linux operating systems is chosen from the menu.

Each operating system then can keep the bootloader that is peculiar to it within its own partition. If the kernel, filesystem, or bootloader for one OS changes, it does not affect the ability of any other operating system to start, nor will it affect the primary Grub bootup menu (which is stored and protected within its own boot partition).

This avoids the otherwise common problem that whenever a new OS (or distribution) is installed (including Ubuntu), it stores a Grub configuration menu within its own partition and takes over the functions of the bootloader for every other OS. If there are multiple operating systems, it becomes difficult to remember which operating system's bootloader is the currently active one (that the Master Boot Record points to). With the chainloading method, you don't have to worry about that, anymore. You can upgrade or replace any OS and not worry about disturbing the ability of any other OS to load.


I'm VERY interested in Multi-OS-Booting and even more interested in the above idea.

My question(s):

1) If I'm not mistaken, the above idea is for Legacy GRUB. Can we have the same scheme with GRUB2?

2) If the answer of Q1 is YES then what's the difference between this idea and another idea which is: Installing the boot loader of each OS in its own partition/HDD?

3) If the answer of Q1 is NO then what's the advantages and disadvantages of having the boot loader of each OS on its own partition/HDD?

4) Which version of GRUB is better? the legacy version (AKA GRUB) or GRUB2 (1.97)? some say GRUB is easy to maintain or configure but I find GRUB2 easy to use.

5) Any recommendation/suggestions for the best tool(s) that I could use to deal with Windows issues like booting and stuff? I know about GParted, Partition Magic and I used both. Of course I used Windows Disk Manager but ... are there any other tools which are better?

That's all for now :)

Thanks a lot!

---

### Post by oldfred on 2010-10-07
I still have my grub legacy partition and it boots one or two older install. Grub legacy installed to the partition boot sector (PBR) without complaint and chainloading worked well for me. 

Eventually I converted to grub2, some users here wondered why I was still chainloading, but I was still learning grub2 and had several partitions booting grub legacy. Now I do not have much grub legacy stuff left and grub2 osprober is so good at finding other systems you do not need to install a boot loader into the PBR. If it is an older system that still uses grub legacy you can chainload from grub2. I have several drives and chainload between them to the MBR not PBR, but the drive number changes depending on which drive is first in BIOS as it will always be hd0. So  chainloading to hd1 may not be the drive I thought it was.

Grub2 also does not like to be installed to a PBR. They have to use blocklists which are hard coded addresses and not file lookups.

Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

---

### Post by HermanAB on 2010-10-07
Howdy,

Multi-boot is useful, but it is a very 20th century concept.  For most applications, it is better to install VMware Player or Virtualbox and making a virtual machine for the other systems that you need.  The advantage is that you can then them all at the same time.

---

### Post by amjjawad on 2010-10-09
> **oldfred said:**
> I still have my grub legacy partition and it boots one or two older install. Grub legacy installed to the partition boot sector (PBR) without complaint and chainloading worked well for me. 

Eventually I converted to grub2, some users here wondered why I was still chainloading, but I was still learning grub2 and had several partitions booting grub legacy. Now I do not have much grub legacy stuff left and grub2 osprober is so good at finding other systems you do not need to install a boot loader into the PBR. If it is an older system that still uses grub legacy you can chainload from grub2. I have several drives and chainload between them to the MBR not PBR, but the drive number changes depending on which drive is first in BIOS as it will always be hd0. So  chainloading to hd1 may not be the drive I thought it was.

Grub2 also does not like to be installed to a PBR. They have to use blocklists which are hard coded addresses and not file lookups.

Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

No offense but this is an advanced post to me. I need to learn and rear more to understand all this :( sorry!
But thanks anyway :)

---

### Post by amjjawad on 2010-10-09
> **HermanAB said:**
> Howdy,

Multi-boot is useful, but it is a very 20th century concept.  For most applications, it is better to install VMware Player or Virtualbox and making a virtual machine for the other systems that you need.  The advantage is that you can then them all at the same time.

Hey :)

I've never tried VMware nor Virtualbox. I've read some where here in this forum that I need big size of RAM? is that correct?
Oh thing I'd like to know. What are the real advantages of VMware and/or Virtualbox? what are the disadvantages?

---

### Post by amjjawad on 2010-10-09
Honestly, I'm still waiting for more replies about my questions.

I tried something and it worked perfectly so far except I didn't put the final touch :)

I have a Multi-OS-Booting System now on my machine. GRUB2 is amazing to find other OS's. One command and that's all.
So far, GRUB2 (in Ubuntu) is installed on an external HDD.
I installed 7 Operating Systems and the boot loaders of all of them are located in each OS's partition where that particular OS is installed. *Check my signature.*

So, non of these 7 Operating Systems has its boot loader in the MBR.
So far, the only way to boot into one of these 7 is to turn the external HDD ON and make sure it's the first device to boot from.
I know it's not efficient and not that much smart but that's a temporary solution and I know how to fix it and I'll. It's not a problem actually. I turn it off when I want to use WinXP. Windows XP has its own HDD and of course its boot loader is installed on the MBR. If the external HDD is off, my PC will boot into WinXP. I have NO problem with that at all.
The only annoying thing is to keep the external HDD on and as I mentioned, I'll fix it and it's not a big deal.

The only thing that I haven't try is to create a partition for the boot loader. I have no clue whether this is going to work with GRUB2 or not?!

One other thing I did and I'm not sure if it's correct move or not.
ALL the 7 OS's are sharing the same SWAP partition. Is this fine?

I also read some where that I could make another shared partition for all OS's and that is /data. Right?

So, few more Qs to the main questions listed on the first post :)

---

### Post by perspectoff on 2010-10-10
> **oldfred said:**
> 
Attempting to install GRUB to a partition instead of the MBR. This is a BAD idea.
Embedding is not possible, GRUB can only be installed in this setup by using blocklists. However blocklists are UNRELIABLE and its use is discouraged.
error: If you really want blocklists, use --force

I think this is nonsense.

The Master Boot Record is merely a register that indicates which partition has the initial bootloader to be used. It is not a directory.

GRUB2 gets installed into the partition in which the Ubuntu OS is installed. During installation Ubuntu sets the MBR to point to that partition. If that partition is changed, deleted, moved, or renumbered, you are sunk.

Further, if that partition gets screwed up, you also won't be able to boot up any longer (for any OS). Risky strategy, in my opinion. You are assuming the Ubuntu OS' partition will always be perfect. Hah!

I don't know that much about what GRUB2 requires, but I'll take this poster's word for it that it does not like to exist on a partition that does not have an OS associated with it.

Grub Legacy lives quite happily on its own partition (and does not require an OS to function properly), which is why I continue to use it as the primary bootloader.

I then use Grub Legacy to chainload Grub2 only when loading Ubuntu. I never use Grub2 to chainload the Windows or Mac bootloaders. There are still far too many problems with Grub2, and relying on one OS's bootloader to boot another OS is folly, in my opinion.

PS

The entry in Grub Legacy that I use to chainload Grub2 (which on my system resides in the partition located at /dev/sda7) is:

 title Kubuntu Lucid OS (chainloader)
 rootnoverify (hd0,6)
 kernel /boot/grub/core.img

---

### Post by perspectoff on 2010-10-10
> **amjjawad said:**
>  I'm reading many threads/articles in no time.
While I was searching/reading, I found this:

[https://help.ubuntu.com/community/MultiOSBoot](https://help.ubuntu.com/community/MultiOSBoot)



I wrote most of that article originally and my more up-to-date versions are at:

[http://ubuntuguide.org/wiki/Multiple_OS_Installation](http://ubuntuguide.org/wiki/Multiple_OS_Installation)

and

[http://kubuntuguide.org/Multiple_OS_Installation](http://kubuntuguide.org/Multiple_OS_Installation)

---

### Post by amjjawad on 2010-10-11
Okay, here's the most recent update for this thread.

1) I have the following Operating Systems installed, each on it's own partition and each has its boot loader in that partition. Except for Windows XP (it's boot loader in sdb -MBR) and Ubuntu (it's boot loader in sda -MBR).

> 
Generating grub.cfg ...
Found linux image: /boot/vmlinuz-2.6.32-24-generic
Found initrd image: /boot/initrd.img-2.6.32-24-generic
Found memtest86+ image: /boot/memtest86+.bin
Found Fedora release 13 (Goddard) on /dev/sda10
Found Linux Mint 9 Isadora (9) on /dev/sda11
Found Linux Mint 9 Isadora (9) on /dev/sda12
Found Ubuntu 10.04 LTS (10.04) on /dev/sda13
Found Ubuntu 10.04 LTS (10.04) on /dev/sda14
Found Ubuntu 10.04.1 LTS (10.04) on /dev/sda15
Found Fedora release 13 (Goddard) on /dev/sda9
Found Windows NT/2000/XP (loader) on /dev/sdb1
done


2) I no longer use the external HDD to boot my system. I turned it off and I installed fresh copy of Ubuntu on sda (500GB SATA HDD) so all Linux Distributions are on sda.

3) ALL Linux Distributions are sharing the **SWAP Partition**. I tried to create a swap partition during the step of the 2nd OS but the installed detected two swap partitions. At that point, I removed the created swap partition and used the existing one. After that, each time I install a new OS (Linux), the installer had to format the swap partition every time.

4) Only Ubuntu has /home partition. All the other Linux Distributions have / and shared swap partition.

Now ... these are my new questions:

A- I had ONE SWAP partition for all the above OS's (except Windows XP). I  was wondering if this is okay and there will not be any problems/issues  with that? I think it's not a bad idea but of course this is my first month with Linux so I need to hear from expert people :)

2- Let's say I want to create a separate boot partition (as mentioned  before) but instead of using Legacy GRUB, I'll use GRUB2. Do you think  there's any need to that? I mean, as long as GRUB2 is finding all the  other OS's and as long as with one simple command, I can find any other  new OS or update the list in case I removed one OS so ... I think the  GRUB2 is already doing the job. The only difference is instead of having  it's own partition, it's on the root partition of Ubuntu. 
It seems I already know the answer for this question (No need to have a  separate partition for the boot loader) but I just want to discuss it  with you [IMG]http://forums.fedoraforum.org//forum/images/smilies/smile.gif[/IMG]

[B]So bottom line: that method of *creating a separate partition and use the legacy GRUB to boot and find all the other boot loaders of the installed OS's in a Multi-boot system* is just an extra step in case I'm using GRUB2 and it's already installed in the MBR. Point is, as long as GRUB2 is finding all the other OS's and it's the master boot loader of all the others, I don't think there's any need to create a separate partition. What do you think?

[/B]The best thing is >> if I ever have to remove one of the 8 OS's which are all Linux Distros, I don't need to worry about anything. GRUB2 in a single commend can update the list. Even if I have to remove Ubuntu, I could still use my external HDD. If you remember, first, I had Ubuntu installed there but had to keep it on every time I want to boot into another OS. 
So the only case I won't be able to boot the other Linux Distros is when Ubuntu (GRUB2) will be removed and something wrong will happen to my external HDD where another copy of Ubuntu is already installed. That's not going to happen anyway because I can simply install another copy on sda (where all the Linux Distro exist) and ask the installed to install the boot loader in the MBR of sda.

I hope this is not confusing. Again, I know I asked the question and answered it but I still want to hear your opinion.


3- In Ubuntu, there's no **/data** partition, unlike Fedora. On the other hand, there's **/home** partition and I have it on a separate partition of course. 
a) is it good idea to share that /home partition with all the other 7 Linux Distros?
b) if it's good idea, will that /home partition be sharable and  accessible by the other OS's? in other words, can I use that /home  partition as /home for each OS? just like the swap partition is now  sharable with all the OS's I have?

That's all for now :)

Thanks!

---

### Post by oldfred on 2010-10-11
With grub2 you do not need a grub or boot partition. Either of those would also require manual editing of the grub.cfg or menu.lst. The one disadvantage of one boot loader is if you have a new kernel in one of the other distributions you have to boot Ubuntu and run the update grub to see the newest kernel. But ranchhand posted a workaround that uses the link to the most current kernel in /. Not sure if all other installs do this.

From Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

Change to your drive & partition:
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

You do not share /home across distributions nor share within Ubuntu. You use it for upgrading as the newer version of software knows to update its settings. But older versions of software may have issues with new settings. Other distributions may all have different versions of software.

What you do want is a /data partition with all your data but not your user settings. You can easily mount it in every distribution with fstab and link your data folders into /home in place of the standard folders.

Partitioning basics with some info on /data older but still relevant
[http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition](http://ubuntuforums.org/showthread.php?t=282018&highlight=separate+%2Fdata+partition)

Painless Linux Multi-boot Setup - see also comments by Morgan Hall
[http://blog.linuxtoday.com/blog/2009/08/painless-linux.html](http://blog.linuxtoday.com/blog/2009/08/painless-linux.html)
oldfred's versions (post #5) of data linking from above blog, based on more from comments 
[http://ubuntuforums.org/showthread.php?t=1405490](http://ubuntuforums.org/showthread.php?t=1405490)

How to Multi-boot (Maintain more then 2 OS) old grub
[http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by amjjawad on 2010-10-17
> **oldfred said:**
> With grub2 you do not need a grub or boot partition. Either of those would also require manual editing of the grub.cfg or menu.lst. 

What kind of editing?

> 
The one disadvantage of one boot loader is if you have a new kernel in one of the other distributions you have to boot Ubuntu and run the update grub to see the newest kernel. 
I don't mind to type:

```

sudo update-grub

```If that's all what I really need to do.

> 
But ranchhand posted a workaround that uses the link to the most current kernel in /. Not sure if all other installs do this.

From Ranch hand
Note that this does not define the kernel. It defines the partition. It boots the newest bootable kernel that it finds at that partition.

Change to your drive & partition:
menuentry "Daily on sda13" {
    set root=(hd0,13)
        linux /vmlinuz root=/dev/sda13 ro quiet splash
        initrd /initrd.img
}

Was that BASH code or something?
I don't want to mess around with booting because every time I try that, I lose something so better to keep everything as it's as long as it's working without any problem. After all, I'm trying that kind of setup because this is the first time for me to install and boot 9 OS's at the same time.
Beside, I didn't understand much what that code does anyway.

> 
You do not share /home across distributions nor share within Ubuntu. You use it for upgrading as the newer version of software knows to update its settings. But older versions of software may have issues with new settings. Other distributions may all have different versions of software.
I have /home partition ONLY with Ubuntu. For the other distributions, I don't have /home partition. I've done that because (as I mentioned earlier) I'm trying that kind of setup (Multi-OS-Boot) and I don't need that much of /home partitions at the moment.
And yes, I think sharing /home with other OS's is bad idea.

> 
What you do want is a /data partition with all your data but not your user settings. 
I have now 100GB NTFS Data Partition that all my OS's should be able to access it.
I was wondering how do I make it auto-mounted every time I boot? is it possible? 

> 
You can easily mount it in every distribution with fstab and link your data folders into /home in place of the standard folders.
???
I didn't get it!

---

### Post by oldfred on 2010-10-17
You need to understand mounting and setting fstab to always mount a partition.

Understanding fstab
[http://ubuntuforums.org/showthread.php?t=283131](http://ubuntuforums.org/showthread.php?t=283131)
Ownership and permissions of vfat / ntfs are set at the time of mounting. This is often a source of confusion.
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

Only after you understand the above should you use this as it may not always give you the correct settings unless you understand what you want.
I prefer the control manual editing gives, but
Some think it is a lot easier to use a graphical front end that both creates the mount point and edits fstab.
Try installing pysdm from the repos.
PySDM is a PyGTK Storage Device Manager
GUI Fstab Editing with PySDM 
[http://ubuntuforums.org/showthread.php?t=872197](http://ubuntuforums.org/showthread.php?t=872197)

---

### Post by amjjawad on 2010-12-12
Oldfred, one day, we should finish our interesting discussion about this :D
Every time I want to post here, I got busy with something else and forget about it. I know I could answer most of the questions here but I'd love to keep talking about this if you don't mind.

If you think it's a bad idea, then forget it.

Edit: I'll mark this thread as SOLVED :)

---

