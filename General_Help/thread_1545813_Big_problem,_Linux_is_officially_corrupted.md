---
title: "Big problem, Linux is officially corrupted"
date: 2010-08-04
forum: General Help
---

### Post by kmccmk9 on 2010-08-04
Well I seemed to have corrupted linux so badly. I can no longer log in. No colors its really bad. All I did was try to get rid of the original problem. PulseAudio. So is there anyway to recover my linux. I really don't want to lose everything and try to remember all of the applications I had installed. Is there something I could do with a live cd or is the a recovery disc? All I need is something to reinstall the basic files. I believe centered on Audio and Display

---

### Post by realzippy on 2010-08-04
Can you start in recovery mode?
Then drop to root shell and reinstall the package ubuntu-desktop:

```
apt-get install ubuntu-desktop
```

---

### Post by mike555 on 2010-08-04
You will need to reinstall, but if you use the live cd to copy your installed file  /var/cache/apt/archives to an external USB drive , it will help you install whatever you had installed .......... you can also copy your /home folder ...

---

### Post by kmccmk9 on 2010-08-04
> **realzippy said:**
> Can you start in recovery mode?
Then drop to root shell and reinstall the package ubuntu-desktop:

```
apt-get install ubuntu-desktop
```

Thanks that worked but my drivers still seem to be screwy so I think I may do a complete reinstall but save the things I have downloaded like the other post says.

---

### Post by kmccmk9 on 2010-08-04
Ok well I can't seem to install into the partition. It just doesn't work. Everything I try just keeps telling me root file system not selected. So any help with that?

---

### Post by mike555 on 2010-08-04
When you go to install, pick the partition and set it as " / " ......... that sets it as root.

---

### Post by WorMzy on 2010-08-04
> **kmccmk9 said:**
> Ok well I can't seem to install into the partition. It just doesn't work. Everything I try just keeps telling me root file system not selected. So any help with that?

Are you in the process of reinstalling? If so, I assume you chose to manually partition your drive; in which case you need to select a partition to be used as the "/" (or root) of the Ubuntu installation. To do this, just double click on the existing (broken) Ubuntu partition, and change the "Use as" field to "/". (You'll have to forgive me if the labels are different, it's been a while since I last used the Ubuntu installer) You may also want to designate a swap partition, though that isn't necessary.

---

### Post by celldweller1591 on 2010-08-04
> When you go to install, pick the partition and set it as " / " ......... that sets it as root.
It should be working by default !! inst it ?

---

### Post by kmccmk9 on 2010-08-04
should I format the partition? It game me a warning before it did it so I haven't done anything yet. 

"The file system on /dev/sdb5 assigned to / has not been marked for formatting. Directories containing system files (/etc, /lib, /usr, /lib ...) that already exist under and defined mountpoint will be deleted during install."

---

### Post by WorMzy on 2010-08-04
It's up to you. Making the partition for formatting is less likely to cause problems than not marking it for formatting, but the risk is negligible either way. If you don't mark it, then there's a chance that your /home folder contents will still be there after the installation.

---

### Post by kmccmk9 on 2010-08-04
Ok so I didn't mark it and it tells me everything will be deleted?

---

### Post by WorMzy on 2010-08-04
System directories will have their contents removed before installation begins, but I'm not sure about /home. If it's telling you that everything will be deleted, then you may as well just check the format option.

---

### Post by kmccmk9 on 2010-08-04
> **WorMzy said:**
> System directories will have their contents removed before installation begins, but I'm not sure about /home. If it's telling you that everything will be deleted, then you may as well just check the format option.

Ok thank you for all your help. Hopefully this comes out right. I don't think I will ever use PulseAudio again lol

---

### Post by kmccmk9 on 2010-08-04
> **WorMzy said:**
> System directories will have their contents removed before installation begins, but I'm not sure about /home. If it's telling you that everything will be deleted, then you may as well just check the format option.

Ok I ran into another problem. During install it is asking what I want to do with the grub. What should I choose here?

---

### Post by oldfred on 2010-08-04
You want to install grub to the drive not partitions. I think the new version now only gives drives and the Ubuntu partition as choices. If Ubuntu is on sda choose sda, or whatever drive your install is on.

---

### Post by kmccmk9 on 2010-08-04
> **oldfred said:**
> You want to install grub to the drive not partitions. I think the new version now only gives drives and the Ubuntu partition as choices. If Ubuntu is on sda choose sda, or whatever drive your install is on.

Um ok this is the options I am getting.

"Configuring grub-pc. A new version of configuration file /etc/default/grub is aavailable, but the version installed currently has been locally modified. 

Options-
Install the package maintainers version
keep the local version currently installed
show the differences between the versions
show a side-by-side difference between the versions
show a 3-way difference between available versions
do a 3-way merge between available versions  (experimental)
start a new shell to examine the situation "

p.s. also just so you know this is when I am trying to upgrade to the latest Linux using Update Manager

---

### Post by WorMzy on 2010-08-04
Just choose "Install the package maintainers version" unless you've manually made any changes to that file that you need to keep.

---

### Post by kmccmk9 on 2010-08-04
> **WorMzy said:**
> Just choose "Install the package maintainers version" unless you've manually made any changes to that file that you need to keep.

I didn't make any changes that I know of. Except I installed Ubuntu before then updated it created two kernals. But I didn't do anything so is that what it is talking about?

---

### Post by kmccmk9 on 2010-08-04
> **WorMzy said:**
> Just choose "Install the package maintainers version" unless you've manually made any changes to that file that you need to keep.

New problem I know have to choose which devices to install grub-pc on. One is the first hard drive with windows. Second is the second hard drive partitioned windows . Third is Partition which linux is installed. WHich ones do a mark?

---

### Post by WorMzy on 2010-08-04
I don't use the version of grub that you're using (Grub 2), but I believe that you should just install it onto the _disk_ that is first in the BIOS boot order, rather than a specific partition. This will most likely be sda.

If you open a terminal and run ```
sudo fdisk -l
``` it'll show a table in the terminal with an asterisk (*) next to the partition(s) which the BIOS looks at for the MBR ([Master Boot Record]("http://en.wikipedia.org/wiki/Master_Boot_Record")). If you want to install grub to a specific partition, the one(s) with asterisks next to their identifier are your best bet.

---

### Post by kmccmk9 on 2010-08-04
> **WorMzy said:**
> I don't use the version of grub that you're using (Grub 2), but I believe that you should just install it onto the _disk_ that is first in the BIOS boot order, rather than a specific partition. This will most likely be sda.

If you open a terminal and run ```
sudo fdisk -l
``` it'll show a table in the terminal with an asterisk (*) next to the partition(s) which the BIOS looks at for the MBR ([Master Boot Record]("http://en.wikipedia.org/wiki/Master_Boot_Record")). If you want to install grub to a specific partition, the one(s) with asterisks next to their identifier are your best bet.

Ok I got it thanks.

---

### Post by WorMzy on 2010-08-04
Glad to hear it. :)

Enjoy Ubuntu! :D

---

### Post by 3rdalbum on 2010-08-04
In the future, bear in mind that removing parts of the core system will generally cause problems unless you REALLY know what you're doing.

---

