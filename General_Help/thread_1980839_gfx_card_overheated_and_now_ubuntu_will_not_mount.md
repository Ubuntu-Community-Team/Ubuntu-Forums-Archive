---
title: "gfx card overheated and now ubuntu will not mount"
date: 2012-05-15
forum: General Help
---

### Post by domtron on 2012-05-15
Hello I’m having a problem with my ubuntu install. 
ubuntu 11.04 LTS

My problem started with the fan on my gfx card dieing from dust. As a quick fix I’ve been using a regular house fan (extremely noisy as you might imagine). School had just gotten out for the summer and cleaning the dust out was on my to do list. However the gpu started overheating even though I had the house fan on it. When it overheats it automatically shuts down the gpu and the screen goes black with a no signal message. So I have to shut down the computer manually. I let it cool off and turned up the fan then turned the computer back on. It overheated again less then 20 minutes later. I took out the gfx card and vacuumed out the dust (I had done this before and it fixed the fan). After a third failed attempt(I couldn‘t get the fan working) I took an old CPU fan and spliced it into one of the power cables so it could cool the gpu(the fan did run). However when I booted the computer up again I got this message(after grub):

1. Mount: mounting /dev/disk/by-uuid/03dfo843-1a46-4b71-8d0d-25cd741f4268 on /root failed: Invalid Argument
2. Mount: mounting /dev on /root/dev failed: no such file or directory
3. Mount: mounting /sys on /root/sys failed: no such file or directory 
4. Mount: mounting /proc on /root/proc failed: no such file or directory
5. Target file system doesn’t have /sbin/init
6. No init found. Try passing init = boottarg

7. Busybox v1.13.3 (ubuntu 1:1.13.3-1ubuntu11) builtin shell
8. (initramfs) >

 ls in / shows that dev, sys, proc, and sbin (along with several other directories) are present.

I’m not sure if I should try reinstalling ubuntu. The really wired thing is the gfx card is overheating when there’s only a shell running >.< I can get into windows fine (dual boot) and it doesn’t over heat the gfx card (windows has been running fine for about 3 hours). Any help would be appreciated.


Summery:

ubuntu 11.04 LTS
Gfx card overheats in Linux(even in the shell!) but not windows.
Booting linux gives mounting errors and never gets to the desktop.

If it helps any I tried to play mine craft, it gave me a odd error message then the gfx card started overheating.

---

### Post by UltimateCat on 2012-05-15
There is a special kind of gloves that you can wear to touch the internal circuity of your computer.

It may be a good idea for you to gently wear them and lightly touch and clean out the dust.

Best Buy might be a good place to consider, Tiger Direct or maybe even New-egg.com

These are just suggestions but it sounds like the dust might be taking over your system.

Linux might be of help too: linuxquestions.org

Best of luck to you with what you decide-

---

### Post by domtron on 2012-05-16
Thanks for the quick reply. 

I must have emphasized the gfx card too much. My primary concern right now is the inability to boot into linux at all. I asked a friend and he seemed to think it was a problem with grub.
Could I try re-installing Ubuntu without losing my files and settings?

---

### Post by hal8000 on 2012-05-16
Its strange that you can boot windows without overheating.

What is your graphics card make / model?


You may be able to get into your linux system by booting the
live Ubuntu CD.

Boot with the CD in live mode, then post the output of:

fdisk -l

---

### Post by domtron on 2012-05-16
Here is the gfx card information:
Radeon HD 4830 512MB GDDR3 PCIe 11147-00-20R
[http://www.testseek.co.uk/computers/graphic_cards/pci-express/sapphire_radeon_hd_4830_512mb_gddr3_pcie_11147-00-20r-p-0c04f890-3d61-d0b8-d02d-72521e5d4f34.html?start=20](http://www.testseek.co.uk/computers/graphic_cards/pci-express/sapphire_radeon_hd_4830_512mb_gddr3_pcie_11147-00-20r-p-0c04f890-3d61-d0b8-d02d-72521e5d4f34.html?start=20)

ok I booted up in the live CD and ran the following

I have been using the gfx card with ubuntu for a while. I think I did a system update recently.
I have a number of old gfx cards that I can try. However, I didn't want to introduce anymore variables before consulting someone else. 

fdisk -l
Cannot open /dev/sda

ls /dev | grep sda
sda
sda1
sda2
...
sda8


Thanks

---

### Post by MutantJohn on 2012-05-17
I think if it can't open /dev/sda then I think that means it can't open your hard drive. But I don't know, actually. This is my first time actually trying to help someone with a reply but if it's telling you there's an issue with /dev/sda then it's your hard drive and not your GPU. Maybe.

---

### Post by domtron on 2012-05-17
I wasn't saying that my gfx card overheating was a direct cause of the booting trouble, but rather an indirect cause that forced me to repeatedly reboot the computer. I think the forced reboots must have corrupted a file so it can not boot, or it might have even corrupted the entire linux file system(I fervently hope not >.<) but not the hard drive since I can still boot up windows. I have no clue if that is possible or not. 

I think I'm going to need to re-install Ubuntu and I need to know if I can save the files that are on the hard drive.

---

### Post by grahammechanical on 2012-05-17
I cannot say for sure but Windows and Ubuntu may use different methods of obtaining the monitor settings. Windows may be using a configuration file. I do not know if that is the case.

Ubuntu (X-server) uses the graphic card to interrogate the monitor to obtain the optimum settings. I think that it does this at every boot rather than reading a configuration file. This is why we are able to change monitors without going through some Add New Device utility.

I once had a graphic card overheat. At first I could go into low resolution mode. Then, I could not load Ubuntu at all. The live Cd would not run. I could not install. I too thought that Linux was messed up.

I was able to install a 2007 version of Mandriva because it required me to set a screen resolution during the install. 

Ubuntu does not requires us to set the monitor settings. Have we noticed that? I concluded that the video card was not passing the monitor settings to the X-server.

I purchased a new graphic card to solve my problem. You might be able to solve your problem by manually editing the X-server configuration file and setting screen resolution and that kind of stuff.

Regards.

---

### Post by domtron on 2012-05-17
Thanks for that quick lesson on hardware detection I didn't know that. 

I can boot into the live CD, but the desktop is out of proportion (Live CD tries to display a square desktop on a rectangular monitor.) How can I change the x-server configuration? If it's handled by grub I probably could, but if it is on the hard drive I have no way of accessing it.

---

### Post by cryptotheslow on 2012-05-17
You need to run that fdisk command using sudo to get any meaningful output.

So:
```
sudo fdisk -l
```

---

### Post by domtron on 2012-05-17
Ok this is odd. I booted up the live cd and ran both fdisk -l and sudo fdisk -l. This time I got more then just "cannot open /dev/sda".


```
ubuntu@ubuntu:~$ fdisk -l
Cannot open /dev/sda

Disk /dev/sdb: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x7b087936

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7765     7827088+   b  W95 FAT32


ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1549f232

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       29916   240300238+   7  HPFS/NTFS
/dev/sda2           59476       60801    10651095    7  HPFS/NTFS
/dev/sda3           29917       59415   236950687    5  Extended
/dev/sda5           29917       30755     6731280   83  Linux
/dev/sda6           59354       59415      497983+  82  Linux swap / Solaris
/dev/sda7           30755       58604   223696896   83  Linux
/dev/sda8           58604       59353     6023168   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sdb: 8015 MB, 8015282176 bytes
32 heads, 63 sectors/track, 7765 cylinders
Units = cylinders of 2016 * 512 = 1032192 bytes
Disk identifier: 0x7b087936

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        7765     7827088+   b  W95 FAT32

```

---

### Post by cryptotheslow on 2012-05-17
It looks like you have 2 Linux installs on /dev/sda (sda5 and sda7).

Can you post up the output to:
```
sudo blkid
```

We should then be able to match the relevant partition to the uuid in your first post.

---

### Post by domtron on 2012-05-18
Here is the results of blkid

```
ubuntu@ubuntu:~$ sudo blkid
/dev/sda1: UUID="EC2EE6672EE62A72" LABEL="COMPAQ" TYPE="ntfs" 
/dev/sda2: UUID="949CA48C9CA46A86" LABEL="FACTORY_IMAGE" TYPE="ntfs" 
/dev/sda5: UUID="1efa8a73-187d-4735-8d58-609f5b76e9e5" SEC_TYPE="ext2" TYPE="ext3" 
/dev/sda6: UUID="2d4752f5-de47-48bd-bb91-b226cd27f41f" TYPE="swap" 
/dev/sda7: UUID="03df0843-1a46-4b71-8d0d-25cd741f4268" TYPE="ext4" 
/dev/sda8: UUID="9e182abc-0981-4e46-9564-977e2a5e932b" TYPE="swap" 
/dev/loop0: TYPE="squashfs" 
/dev/sdb1: LABEL="HP V125W" UUID="5AB8-C73B" TYPE="vfat" 

```

I believe the first two relate to the windows install.

---

### Post by cryptotheslow on 2012-05-20
Judging from the error you posted in your first post your current install is in /dev/sda7

As you say it may well have become corrupted doing all the reboots particularly if you were having to use the power button to turn off.


So first off, try to check for and fix any filesystem errors. Boot to the LiveCD and from Terminal:

```

sudo e2fsck -fpv /dev/sda7

```

Then try rebooting into the installation and see if it works.

If not, boot back to the LiveCD and try to rescue your files:

```

sudo mount /dev/sda7 /mnt

```

If this is successful your installation partition is now available at /mnt in the LiveCD filesystem. So:

```

gksu nautilus

```

To open a file explorer with admin privileges and browse to /mnt/home and into your user directory to find your files - copy them off to a usb stick or whatever.

If you get any errors during any of this post them back here and we'll try to help :)

---

### Post by domtron on 2012-05-21
I just remembered some information that might be helpful. My computer is a 64-bit as is my Linux install. However the windows install was preloaded and for some reason they installed a 32-bit version(its btw vista).

---

