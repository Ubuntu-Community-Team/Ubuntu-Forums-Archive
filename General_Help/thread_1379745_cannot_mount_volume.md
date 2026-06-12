---
title: "cannot mount volume"
date: 2010-01-12
forum: General Help
---

### Post by sharksdad on 2010-01-12
Hello,

I am running a Dell desktop that is Dual booting Vista and Ubuntu 8.04. I mainly use, mostly use Ubuntu, but recently tried to use Vista. It would not boot at all, instead of a blue screen, i simply have a black screen that goes no where. 

I booted into Ubuntu, and tried to get in that way when I received a message that states,
Cannot mount volume.

I did some investigating and opened a terminal and ran the following with these results

family@family-desktop:~$ sudo mkdir /media/sda1
[sudo] password for family: 
family@family-desktop:~$ sudo mkdir /media/sda1
mkdir: cannot create directory `/media/sda1': File exists
family@family-desktop:~$ sudo mount -t ntfs-3g  /dev/sda1  /media/sda1 -o defaults,umask=0
NTFS signature is missing.
Failed to mount '/dev/sda1': Invalid argument
The device '/dev/sda1' doesn't have a valid NTFS.
Maybe you selected the wrong device? Or the whole disk instead of a
partition (e.g. /dev/hda, not /dev/hda1)? Or the other way around?
family@family-desktop:~$ ls /media/sda1
family@family-desktop:~$ 

At this point, I want to get back into Vista so I can recover my wifes photos of our kids and then finally wipe it out, but I need to get in. Does anyone have some help for me. Understand, I have been using Ubuntu for 2 years now, but am not a tech by any means so be kind.

Thank you

---

### Post by Leppie on 2010-01-13
download the vista recovery disk: [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)

---

