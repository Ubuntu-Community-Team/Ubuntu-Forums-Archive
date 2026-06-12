---
title: "Help!!!"
date: 2010-02-04
forum: General Help
---

### Post by MSR3 on 2010-02-04
ok, i have a serious problem and cant get into my computer. It just says

"Grub Loading.
error: unknown filesystem
grub rescue>"

i have windows vista and installed ubuntu 9.10 onto my computer but then didnt want it anymore and so deleted the partition it was in using the vista part of my pc. i then rebooted my computer and this message came up. I can do anything to get in. I have tried to re-installed ububntu using the cd to try and access vista but i thinkl the vista part has been deleted as in the ubuntu istallation, the bit about partitiions it doesnt say vista anymore.

i seriously need help to get vista back up and access my files thank you

---

### Post by audiomick on 2010-02-04
You are booted into Ubuntu now, aren't you?

Open a terminal and do
```
sudo fdisk -l
```that is a lower case L, not a figure one.

Post the output here.

---

### Post by MSR3 on 2010-02-04
> **audiomick said:**
> You are booted into Ubuntu now, aren't you?

Open a terminal and do
```
sudo fdisk -l
```that is a lower case L, not a figure one.

Post the output here.


no i am using my sisters computer

---

### Post by howefield on 2010-02-04
Are you able to load up the live cd to the desktop, and go to System > Administration > GParted and post a screenshot of your disk ?

---

### Post by Leppie on 2010-02-04
boot off a livecd/liveusb and issue the following commands to restore the mbr to factory defaults:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
```
if you're booting off a livecd a warning will appear after the first command, you can just ignor it.
after this your pc should boot into windows straight away.

---

### Post by MSR3 on 2010-02-04
where do i get the live cd? is it the same as the file cd that i downloaded ubuntu on?

i am sorry but i dont knoe much about computers

---

### Post by howefield on 2010-02-04
> **MSR3 said:**
> where do i get the live cd? is it the same as the file cd that i downloaded ubuntu on?

Yes, Try to boot with it, you'll soon know if it does/doesn't.

---

### Post by MSR3 on 2010-02-04
i have loaded the cd what now?

---

### Post by howefield on 2010-02-04
Open a terminal (Applications > Accessories > Terminal) and try the two commands Leppie gave.

---

### Post by MSR3 on 2010-02-04
ok give me a minute....

---

### Post by MSR3 on 2010-02-04
i cant access the internet for some reason...

---

### Post by Leppie on 2010-02-04
not going anywhere ;)

---

### Post by MSR3 on 2010-02-04
please dont leave now!

---

### Post by MSR3 on 2010-02-04
i cant connect to the internet

---

### Post by howefield on 2010-02-04
Go to System > Administration > GParted and take a screen shot of your disk, pressing the alt key along with printscreen key will take a shot of that window.

Post it back here, just to check you still have a windows partition, that you mentioned you think you over wrote.

---

### Post by Leppie on 2010-02-04
> **MSR3 said:**
> i cant connect to the internet
don't you have a lan cable lying around somewhere (usually wireless routers come with one).

---

### Post by MSR3 on 2010-02-04
> **audiomick said:**
> You are booted into Ubuntu now, aren't you?

Open a terminal and do
```
sudo fdisk -l
```that is a lower case L, not a figure one.

Post the output here.

Disk /dev/sda: 160.0GB, 160041885696
255 heads, 63 sectors/track, 19457 cylinders
Units= cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e733731

Device Boot           Start            End                 Blocks          Id           System
/dev/sda1                    1        1530              12288000         27           Unknown
/dev/sda2      *       1530       10310             70522795+        7           HPFS/NTFS
/dev/sda3             10310       13567             26162176           f           W95 Ext'd (LBA)
/dev/sda4             13567      19458              47314944           7           HPFS/NTFS
/dev/sda5             10310      13567              26161152            7           HPFS/NTFS

---

### Post by MSR3 on 2010-02-04
> **howefield said:**
> Go to System > Administration > GParted and take a screen shot of your disk, pressing the alt key along with printscreen key will take a shot of that window.

Post it back here, just to check you still have a windows partition, that you mentioned you think you over wrote.


i cant, i am using my sister computer to write this and have my laptop next to me which is the computer im having trouble with

---

### Post by MSR3 on 2010-02-04
> **Leppie said:**
> don't you have a lan cable lying around somewhere (usually wireless routers come with one).


ill check.....

---

### Post by MSR3 on 2010-02-04
i havent got a lan cable

---

### Post by Leppie on 2010-02-04
> **MSR3 said:**
> Disk /dev/sda: 160.0GB, 160041885696
255 heads, 63 sectors/track, 19457 cylinders
Units= cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2e733731

Device Boot           Start            End                 Blocks          Id           System
[COLOR=Red]**/dev/sda1                    1        1530              12288000         27           Unknown**[/COLOR]
/dev/sda2      *       1530       10310             70522795+        7           HPFS/NTFS
/dev/sda3             10310       13567             26162176           f           W95 Ext'd (LBA)
/dev/sda4             13567      19458              47314944           7           HPFS/NTFS
/dev/sda5             10310      13567              26161152            7           HPFS/NTFS
is /dev/sda1 your linux partition?
if so, issue the following command:
```
sudo fsck.ext4 -pf /dev/sda1
```

---

### Post by Leppie on 2010-02-04
> **MSR3 said:**
> i havent got a lan cable
then how did you install your system?

---

### Post by MSR3 on 2010-02-04
> **Leppie said:**
> then how did you install your system?


wireless internet that worked on my computer on vista but not now

---

### Post by MSR3 on 2010-02-04
> **Leppie said:**
> is /dev/sda1 your linux partition?
if so, issue the following command:
```
sudo fsck.ext4 -pf /dev/sda1
```


i deleted the partition and then formated it becuase i thought i would just go back to normal

sda2 is my C: drive
sda4 is my D: drive
and sda5 was the partition i deleted

i cant reinstall ubuntu i am just on the "try ubuntu without changes to your computer" bit of the cd

---

### Post by mcoleman44 on 2010-02-04
I had this happen a couple of weeks ago and when i tried booting to a live cd it wouldn't work.

I could however boot to super Grub Disk. Its a very small iso. Just burn it to a disc, and boot from the disk. 

You can download it here: [http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/)

---

### Post by MSR3 on 2010-02-04
> **mcoleman44 said:**
> I had this happen a couple of weeks ago and when i tried booting to a live cd it wouldn't work.

I could however boot to super Grub Disk. Its a very small iso. Just burn it to a disc, and boot from the disk. 

You can download it here: [http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/](http://download.linux-live-cd.org/Super_Grub_Disk/download/binaries/sgd/cdrom/)


which one in the list is it?

---

### Post by mcoleman44 on 2010-02-04
main bottom.

---

### Post by mcoleman44 on 2010-02-04
So...you're trying to get back in to your windows partition, right?

---

### Post by MSR3 on 2010-02-04
> **mcoleman44 said:**
> So...you're trying to get back in to your windows partition, right?


yes

---

### Post by Leppie on 2010-02-04
> **MSR3 said:**
> i deleted the partition and then formated it becuase i thought i would just go back to normal

sda2 is my C: drive
sda4 is my D: drive
and sda5 was the partition i deleted

i cant reinstall ubuntu i am just on the "try ubuntu without changes to your computer" bit of the cd
then issue the following commands to boot into your windows install:
```
sudo apt-get install lilo
sudo lilo -M /dev/sda mbr
sudo reboot
```you will get a warning after the first command, just ignore it and continue.


or do you want to re-install ubuntu onto your machine?

---

### Post by MSR3 on 2010-02-04
i cant get the internet so i wont work

---

### Post by mcoleman44 on 2010-02-04
What wont work?

---

### Post by MSR3 on 2010-02-04
leppie's commands

---

### Post by mcoleman44 on 2010-02-04
Disregard my previous comment. You're saying apt-get wont work. My bad.

---

### Post by mcoleman44 on 2010-02-04
Once you boot to super grub disk it will give you a choice of what language. when it takes you to the next menu click on windows. When you you get to the next menu click on boot windows. That should take care of your problem.

---

### Post by MSR3 on 2010-02-04
i have burnt super_grub_disk onto a cd what now?

---

### Post by MSR3 on 2010-02-04
sorry didnt see you last reply

---

### Post by Leppie on 2010-02-04
> **MSR3 said:**
> i cant get the internet so i wont work
you can actually download packages from another machine and then use gdebi to install it on your ubuntu machine...
the package is here: [http://packages.ubuntu.com/karmic/i386/lilo/download](http://packages.ubuntu.com/karmic/i386/lilo/download)

---

### Post by MSR3 on 2010-02-04
that wont work either



mcoleman44  i cant boot super grub disk

---

### Post by MSR3 on 2010-02-04
is there anything i can type into grub rescue that sort it out?

---

### Post by mcoleman44 on 2010-02-04
Well crap. What did it say when you tried to boot the disk?

And why cant you download packages on another computer and then install them on Ubuntu?

---

### Post by mcoleman44 on 2010-02-04
At grub rescue> Try typing 
set root=(hd0,0)

---

### Post by MSR3 on 2010-02-04
> **mcoleman44 said:**
> Well crap. What did it say when you tried to boot the disk?

And why cant you download packages on another computer and then install them on Ubuntu?


it just didnt do anything

i havent actually downloaded ubuntu and cant install either

---

### Post by MSR3 on 2010-02-04
> **mcoleman44 said:**
> At grub rescue> Try typing 
set root=(hd0,0)


it just says "not an assignment"

---

### Post by MSR3 on 2010-02-04
i am just running the "try ubuntu with no changes to you computer" part of the installing cd

---

### Post by beany1 on 2010-02-04
if your just wanting a quick fix to get back into windows, use the windows cd, click repair, and either see if it will fix it with the wizard thing, or click cmd prompt and do bootrec /fixboot  - this will re create the windows boot loader..

---

### Post by Leppie on 2010-02-04
> **MSR3 said:**
> i am just running the "try ubuntu with no changes to you computer" part of the installing cd
i don't think that repeating this part will help you solve the issue much...

---

### Post by mcoleman44 on 2010-02-04
This may sound stupid... But did you set your bios to boot the cd first when you tried running super grub disk?

---

### Post by DukeBoxer on 2010-02-04
go to this page, scroll down to "Rescue Mode" and follow the instructions...it happened to me and thats what i did and it worked fine.

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

