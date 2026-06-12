---
title: "Locked into Windows partition on dual boot"
date: 2011-03-29
forum: General Help
---

### Post by Exhack on 2011-03-29
Hi,

I had dual boot on my Asus laptop, Windows and Hardy. Then my Windows XP crashed and the person who repaired installed Windows 7 but didn't preserve the dual boot prompt on startup. I've explored BIOS but there seems no way of accessing my Ubuntu partition that way. Would some kind person point me in the right direction, please.

---

### Post by coffeecat on 2011-03-29
When Windows is installed it automatically writes boot code to the  mbr, overwriting stage 1 of grub.

You were using Hardy? Please confirm - that is important. Hardy uses legacy grub, so you'll need to run some terminal code from the Hardy live CD. But we need to know what partition Hardy was installed to first.

Boot up with the Hardy live CD, open a terminal and post the output of this terminal command:

```
sudo fdisk -lu
```

---

### Post by Exhack on 2011-03-29
Thanks for that. Windows lists two partitions: its own C: drive (NTFS) and a Ubuntu partition which has two sub-patitions. I have no means of identifying them. I was using Hardy. But this was a download. I haven't got a disk, unfortunately.

---

### Post by coffeecat on 2011-03-29
Without a live CD or live USB there is no way of reinstalling grub to the mbr so that you can dual-boot. You need to run Ubuntu in live mode in order to:

1 - identify the Ubuntu partition with fdisk. Windows is useless for this.

2 - install grub to the mbr.

If you don't have an Ubuntu CD then a live CD of another Linux distro will do so long as it has a compatible version of grub. Unfortunately any old legacy grub won't do. Different distros were patching legacy grub differently around Hardy Heron time. Do you have any other Linux distro CDs?

**EDIT**: you can edit the Windows boot manager I believe in order to boot Linux as well as Windows. I have no experience of this.

---

### Post by Exhack on 2011-03-29
I have a screenshot of the Disk Management pane in Windows but I'm not sure how to get it to you.

---

### Post by coffeecat on 2011-03-29
> **Exhack said:**
> I have a screenshot of the Disk Management pane in Windows but I'm not sure how to get it to you.

It won't help. [Windows 7 Disk Management gets confused by Linux partitions.]("http://ubuntuforums.org/showthread.php?t=1675458") But if you really want to post a screenshot, you can use the 'manage attachments' button below the message field for posting.

Besides, Windows doesn't use Linux partition numbering conventions. We need to know whether Ubuntu is on sda2, sda3, sda5, or whatever. And then you would still need an Ubuntu CD to reinstall grub.

---

### Post by oldfred on 2011-03-29
The quick solution may be this:
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

I prefer grub2 if using Ubuntu.

You do know Hardy ends 2011-04.
[http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases](http://en.wikipedia.org/wiki/Ubuntu_%28operating_system%29#Releases)

And you really should have repair/liveCDs for every system you have installed. You should have a windows repair CD. Neosmart offer those. And then you should have a liveCD or LiveUSB of the installed version of Ubuntu.

---

### Post by Exhack on 2011-03-30
Coffeecat: many thanks for your patient perseverance. How about I download Hardy or a distro that has the right Grub, stick it on a CD and go on from there? BTW: What other Ubuntu progs do have the right Grub?

Oldfred: Thank you too. I will try these steps and report back. You are right, of course, about repair/live CDs. I now have one for Windows and look forward to being able to make one for Ubuntu.Oh, and, yes I'm now a fanatic about backing up my data!!!:)

---

### Post by coffeecat on 2011-03-30
> **Exhack said:**
> How about I download Hardy or a distro that has the right Grub, stick it on a CD and go on from there?

Well yes. Apart from oldfred's suggestion of using EasyBCD instead, that is about your only option. I can't stress enough: you have to have a compatible Linux CD to do what you are trying to do. And I agree with oldfred 100% about the need to have repair/live CDs for every system you have installed. 

> **Exhack said:**
>  BTW: What other Ubuntu progs do have the right Grub?

Not, not Ubuntu programs. I was referring to other Linux distros. Some people have the live CDs of Knoppix, Fedora, opensuse, Slax, Mepis or one of a bewildering variety of Linux distros in their collection. One of those may be suitable, with the proviso I made about different distros patching grub differently. Therefore you are better off using the Ubuntu 8.04 disc.

Also - bear in mind the point oldfred made about support for 8.04 ending soon. As soon as you've restored grub to get Hardy booting again you might want to to think about upgrading or, even better, re-installing with a newer version.

---

### Post by Exhack on 2011-04-06
I'd like to add a postscript to this exchange. People who have suffered this setback and who run Total Commander can access their Ubuntu partition by clicking on Network Neighborhood (just to the right of the C:/ prompt), when they will see an entry "Linux drives". Clicking on that should bring up their Ubuntu files, including the contents of their Home folder. One can then copy those files into the Windows panel and burn them onto a DVD. Armed with an Ubuntu ISO one can then, presumably, I haven't tried this yet, do a clean install when Ubuntu will create a new Grub dual boot. Or one can follow the procedure kindly suggested by my mentors above. Anyway, when I've summoned up the necessary fortitude, I shall attempt the manouevre. In the meantime, thanks to all concerned, especislly a benefactor at Rufusz Computer in Budapest who dreamed up the above ploy and would accept nothing for his trouble. He made my day.

---

### Post by oldfred on 2011-04-06
With 9.10 Karmic I converted from 32bit to 64bit and had to do a clean install. I had years of updates/upgrades in my old partition, so I (new drive helped provide room) created new /, /home & data partitions and kept old install in case I needed something. I did need a few settings from /etc where I had manually edited something, but found some default settings changed so I would not suggest copying and old /etc folder into a new install.

If you have installed a lot of applications:
from lovinglinux - use dpkg to list installed apps
[http://ubuntuforums.org/showpost.php?p=7157175&postcount=5](http://ubuntuforums.org/showpost.php?p=7157175&postcount=5)
[http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/](http://kevin.vanzonneveld.net/techblog/article/restore_packages_using_dselectupgrade/)

List Packages
dpkg --get-selections > ubuntu-files
Reinstall
sudo dpkg --set-selections < ubuntu-files && sudo apt-get dselect-upgrade

It will install the new version of all the apps as it is just by package name, but you may want to houseclean. You do not want to reinstall old kernels and for example Ubuntu is converting from OpenOffice to LibreOffice and you probably do not want both. So you should manually edit list before reinstalling all apps. (it is a long list.)

If you do not have a separate /home you need to back it up and now might be a good time to create one. That has all your user settings in mostly hidden files & folders & your user data.

As part of normal backups one user suggested the following:
backup the following:

1. /home (Users' personal files and settings)
2. /etc (System-wide configuration settings)
3. /var/spool/cron/crontabs (Commands which run automatically)
4. The script to generate the backup

I also run the list of installed apps as part of my backup of /home and run a copy of the boot info script just to have partitions & configuration of booting. I also have copies of several hardware listings.

HTML version of info
sudo lshw -html > ~/hardware_info.html && firefox ~/hardware_info.html
 udevadm info --export-db > file.txt
Similarly, if you run
sudo dmidecode >bios.txt
The last one (dmidecode) lists the machine's DMI or SMBIOS table contents in a friendly format. This DMI or SMBIOS contains a description of the system's hardware components and other useful information such as serial numbers and BIOS revision. This is a really powerful command.

---

### Post by Exhack on 2011-04-15
A final note on this very interesting event. I have successfully installed Ubuntu 10.10 on my old Ubuntu partition. I did this by burning an ISO on a disk and justwent ahead with the installation as I had my personal bits and pieces backed up already (see above). The installation did not ask me anything about the size of partitions etc. as used to happen, it just went ahead and did it, presumably having recognised an older version on a separate partition. To my surprise, when I started the programme for the first time, I found 10.10 had neatly parcelled my pictures etc (but not my music)in a separate package. Not only that, but when I rebooted I got a Windows prompt asking me which partition I wanted to load: Windows or Ubuntu. Only when I chose Ubuntu did the Grub menu appear. It seems that everything has got a lot more sophisticated in recent times. Certainly, 10.10 is light years better than 8.04.

It remains for me to thank my mentors for their very valuable help. I just hope this thread helps someone else.

---

