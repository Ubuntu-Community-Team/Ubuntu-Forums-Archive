---
title: "Help, lost access to my PC"
date: 2010-06-07
forum: General Help
---

### Post by LorenG on 2010-06-07
Hello guys,
I have been using Ubuntu Lucid for a while now, and am extremely impressed with it.
In fact I have installed it on different machines.
Yesterday I stupidly :cry: decided to try something different so I have burned the 64 bit version live CD and went on to install Lucid, not on my hard drive, but instead an external 16GB flash drive.
(I wanted to have a USB pen drive with Ubuntu installed in it :cool:, how cool uh? )
I stupidly 8-[ did not disable the hard drives on my machine first, so now, after the installation of Ubuntu, my computer does not boot from the flash drive and neither does boot from the hard drive.

A bit more information on the hardware:
the PC has two hard drives, one (a 1TB raid 0 configuration - 2x500GB) has WinXP and Windows7 installed in it
the second 640GB drive is used for data only.
The 1TB raid configuration has 3 partitions, the first one is used for XP, the second one is used for Windows 7 and the third one is used for data only. I had a Windows boot loader screen allowing me to choose which one to start.

I am now using the computer via the Ubuntu 64 live CD, and I can see that the partitions are all still there and all the data seems to be there too [-o< but now when I start the machine, set in the bios to boot from the raid 0 configuration I get a black screen, with a short cryptic message mentioning the word GRUB.
I suppose, but don't shoot me if I am wrong, that the installation of ubuntu messed up the original MBR and now cannot boot into my original Windows OS.
I don't mind if I failed in my attempt to install Ubuntu on a flash drive, but would like to restore my machine so that i can boot into windows as before.

Can anyone help me fix this? I have no idea what I am doing #-o

Thanks in advance if you can help

---

### Post by LorenG on 2010-06-07
Ok just to add a bit more information:
when I boot up I see the following message:

[B]error : no such device :  xxxxxxxx-xxx-xxxx-xxx-xxxxxxxxx
grub rescue>[/B]

where the device id corresponds to the flash drive

or if I try to boot from the local drive I get this message:

[B]Booting from local disk...
Try (hd0,0): invalid or null
Try (hd0,1): Ext2: _[/B]

---

### Post by an0dos on 2010-06-07
I believe you'll want to try to recover your windows MBR with a Windows 7 install disc. See the tutorial here: [http://windows7themes.net/how-to-fix-mbr-in-windows-7.html](http://windows7themes.net/how-to-fix-mbr-in-windows-7.html)

see also: [http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

---

### Post by LorenG on 2010-06-07
Thanks,

I have used the winXP install CD to get into the recovery console and then used the command fixmbr.
Now everything is back to normal and I can try again installing Lucid on a usb drive, this time I will disconnect the hard drives :KS

---

### Post by arubislander on 2010-06-07
> **LorenG said:**
> (I wanted to have a USB pen drive with Ubuntu installed in it :cool:, how cool uh? )

If that is all you wanted, you should boot into the desktop from the Live CD and then choose Create Startup USB (or something like that) from the Administrator's menu. Have an iso image handy as I'm not sure the Live CD can see the CD it booted from as a source for the image.

---

