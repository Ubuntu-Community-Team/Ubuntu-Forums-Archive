---
title: "Can't Boot w/o First Using Live CD..."
date: 2010-04-30
forum: General Help
---

### Post by casparov on 2010-04-30
Hi, Everyone... 

I installed Lucid (clean) after being v. satisfied w. Karmic.  

Lucid has presented problem after problem, including the most irritating one thus far: I can't boot (system disk error) unless I put the Live CD in (the Karmic version, yet) and select "boot from first disk".  Once that is done the boot proceeds normally. 

Is there anyway out of this?  I have installed and reinstalled w/ the same problem.  Should I reinstall from the Net and not the Live CD?

Utterly lost,

Casp

---

### Post by Stolea on 2010-04-30
Same thing had happened to me some installs ago.
Odds are that your boot sequence is out in the bios. If you have 2 disks there is a chance that grub is on the second disk in the boot sequence. Hence it can't be activated because bios is looking at the first disk. Try changing the boot order.

---

### Post by ajgreeny on 2010-04-30
You can also run ```
sudo grub-install /dev/sda
sudo grub-install /dev/sdb
``` if you have two disks.

That will mean grub is on both disks and whichever is first in BIOS, the system should boot.  There is no problem that I am aware of, of having grub on more than one disk, and I have that on my system at the moment, with grub from Lucid on sdb and grub from Karmic on sda.

---

### Post by casparov on 2010-04-30
Thanks so much for your reading and replying...

Yes, it's v. odd.  I can boot as long as I have the Karmic Live CD in the rack, which gives me the boot from first disk option.

I can always change the boot order in the BIOS--I am sure that's a work-around.  But I would like to avoid making all these switchbacks within the system.

Beyond this, Lucid will not recognize a DVD disk or the DVD-R unit but WILL show the drive within the device mgr.  As of now, I cannot play a DVD.  :(

Any and all help is greatly appreciated,

C.

---

### Post by Stolea on 2010-05-01
My situation here was that I had windoze on one disk and Ubuntu on another. Because Windoze is a must for me (accounting program only available in Win format) I had that disk as disk #1. I installed the grub on the second disk by choice, because I had disasters with grub in the bootsector of the Windoze disk.
I changed the #2 disk to be the first to boot. Grub lists Win7 as a boot option and I can boot into Win7 when I need to.
You say that you did a clean install. Does that mean that you formated the /(root) and /boot partitions? I had once done an install without a format of those partitions. That left bits of  the previous version and I had all sorts of weird stuff happen.
Just a thought.

---

### Post by casparov on 2010-05-01
Yes, thanks so much for that idea, Stolea... 

I bothered to change the boot order in the BIOS to, incredibly, no effect.  

I may try this link: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows) , but, as always, don't know if it will help.  

I am somewhat--not completely, at all--disappointed w/ Lucid.  It is a v. nice OS, but I can't boot it normally and have no DVD function.  I was hoping that a LTS release would be better for me, but, as is, Karmic delivered more.

All Regards,  C.

---

### Post by oldfred on 2010-05-01
If you have reinstalled grub2 perhaps this will show something else:

Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)
Be sure to highlight and use code tags (# in edit panel) to make it easier to read when you post the results.txt.

---

### Post by casparov on 2010-05-02
OldFred... 

Thank-you so much for your reply.

I downloaded the application to my desktop and, according to the instructions on the site, entered this line at the terminal: 

$ sudo bash ~/desktop/boot_info_script055.sh  

[ Here are the site's instructions: Open a terminal (Applications>Accessories>Terminal in Gnome) and type
 sudo bash [path/to/the/download_folder]/boot_info_script*.sh
For example if you downloaded the file to the desktop, use
 sudo bash ~/Desktop/boot_info_script*.sh ]

NOTE: the file name is boot_info_script055.sh  

Unfortunately, this is the persitent result in Terminal: 
bash: /home/whit/desktop/boot_info_script055.sh: No such file or directory 

Do you have any ideas on how to run this script so that I might post it?  

Thanks so much,

C.

---

### Post by john newbuntu on 2010-05-03
Run this from a terminal after booting from liveCD and see if the file exists:
```
ls -l /home/whit/desktop/boot_info_script055.sh
```If it does not exist, did you download the boot_info_script.sh on to your desktop from:
[http://sourceforge.net/projects/bootinfoscript/](http://sourceforge.net/projects/bootinfoscript/)
There is a green section with a download arrow.

---

### Post by SFCampbell on 2010-05-03
> **casparov said:**
> 
I bothered to change the boot order in the BIOS to, incredibly, no effect.  


Please post your computer's output for **sudo fdisk -l** and **sudo cat /boot/grub/grub.cfg**.  That may indicate a problem with your GRUB bootloader.

---

