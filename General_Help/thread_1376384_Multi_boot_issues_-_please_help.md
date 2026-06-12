---
title: "Multi boot issues - please help"
date: 2010-01-09
forum: General Help
---

### Post by ezervoud on 2010-01-09
My kids netbook had a dual boot edubuntu and win xp.
He asked me to upgrade his xp partition to win 7, which I did
Now there is no boot manager but the system boots right in Win 7
Could you please help to get edubuntu back?

---

### Post by Leppie on 2010-01-09
which version of edubuntu?

---

### Post by SecretCode on 2010-01-09
This is quite common. Windows always reinstalls its own boot loader and ignores other installed operating systems.

You can reinstall the boot loader (called GRUB) from a live CD. Details are given here: [RecoveringUbuntuAfterInstallingWindows - Community Ubuntu Documentation](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

I'm not sure if Edubuntu runs from a "live CD" or if you still have it, but if you have a live CD for edubuntu, use that. 

Otherwise, which version of edubuntu did you have? It matters because Ubuntu 9.10, and distributions based on it, use a new version called GRUB 2. If your edubuntu is based on Ubuntu 9.10, download the Ubuntu 9.10 iso and burn it to a CD; if it's older, download and burn the Ubuntu 9.4 iso.

If you can boot a live CD, it will help to see the output of
```
sudo fdisk -l
```

---

### Post by ajgreeny on 2010-01-09
It will depend on the version of edubuntu, and which grub it had to boot it, though I think edubuntu is not being made any more so will probably be 9.04 and use legacy grub.  Whichever it is here is a page which will help, and a possibly more simple txt from me with both grubs' info.

[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

To restore legacy grub for 9.04 and earlier, boot into the ubuntu live CD
open a terminal and run :
    **sudo grub**
This gets you to a simple grub command line.
Then:
    **find /boot/grub/stage1**
This will tell you where your /boot/grub/stage1 is which is needed to boot ubuntu. If you have more than one linux install you may get more than one answer here.  Use the one from which you want to use grub.  Replace the question marks in the following command with the output of the this last command :
    **root (hd?,?)**
[like : root (hd0,1) ,probably]
then:
    **setup (hd0)**
This is where your windows partition and MBR normally is, but if you want grub on another disk, use hd1, etc as appropriate. It's much easier to use the windows MBR and then just change the default boot system later if others in the family demand windows boots by default.
Then:
    quit
Finally reboot, and hopefully you will now have a working grub bootloader.


How to restore the Ubuntu grub bootloader (9.10 and beyond)

Ubuntu 9.10 uses Grub 2, so you need to find out what your drives are using live CD:
    **sudo fdisk -l**
From that you need to find the device name of your Ubuntu drive, something like “/dev/sda5&#8243;.
Still in the terminal, type:
    **sudo mkdir /media/sda5**
    **sudo mount /dev/sda5 /media/sda5**
To reinstall grub:
    **sudo grub-install --root-directory=/media/sda5 /dev/sda**
Push enter and you’re done! Of course you need to replace “/dev/sda5&#8243; and “/dev/sda” with what you found in the fdisk output.

---

### Post by ezervoud on 2010-01-09
It's 9.04 indeed - however since we are talking about a netbook there is no CD, would a USB stick do?

PS. Ok - I think I found what I was looking for and downloading right now ([http://cdimage.ubuntu.com/releases/9.04/release/](http://cdimage.ubuntu.com/releases/9.04/release/))
I'll try it and get back here
Thanks so much all of you

---

### Post by Leppie on 2010-01-09
yes, if you have the ubuntu 9.04 installer on a usb stick that should work all the same.

---

### Post by ezervoud on 2010-01-09
What would be the recommended way of upgrading the windows partition if One had to do it from the beginning?
I could go from XP to 7 only by installing 7 from the ground up and that would mess me up the way it did, is there a precaution I could have taken?
One of my partitions had pqservice on it, would that help in anything?

---

### Post by Leppie on 2010-01-09
no there isn't a way to prevent this. windows os's are selfish, in such that they always check the mbr pointing to their partition and if it's set differently they overwrite the mbr.
if you have to prevent the mbr from being overwritten, you cannot install windows on the drive.

---

### Post by ezervoud on 2010-01-10
:D Good morning to all :D
It was so easy to regain grub
The most painful part was the long await to dl the live cd
Thank you so much ):P

---

