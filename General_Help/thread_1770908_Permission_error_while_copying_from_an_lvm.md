---
title: "Permission error while copying from an lvm"
date: 2011-05-29
forum: General Help
---

### Post by trinimoses on 2011-05-29
Hi all,

I am new to ubuntu.. but have been using centos for years. on friday my email server that was running centos suffered a software raid failure .. making impossible to boot no matter what i have tried.

so the idea hit me to try out Ubuntu... So i have the live disk of 11.04...

did the following :

Install lvm2:
$ sudo apt-get install lvm2

Load the necessary module(s):
$ sudo modprobe dm-mod

Scan your system for LVM volumes and identify in the output the volume group name that has your Fedora volume (mine proved to be VolGroup00):
$ sudo vgscan

Activate the volume:
$ sudo vgchange -ay VolGroup00

Find the logical volume that has your Fedora root filesystem (mine proved 
to be LogVol00):
$ sudo lvs

Create a mount point for that volume:
$ sudo mkdir /mnt/fcroot

Mount it:
$ sudo mount /dev/VolGroup00/LogVol00 /mnt/fcroot -o ro,user

"

I can see the volume and browse it... but for some reason i cant copy from it... any ideas ??

I am trying to copy to my backup drive which is connected via usb.

my email server is zimbra by the way..

I just need to copy of some data please help.

---

### Post by silkworm2.5 on 2011-05-29
Maybe try running Nautilus as root? It might be a permissions problem. Try this in a terminal:
```
sudo nautilus /
```
Then use that to try and recover the data. If it still doesn't work, then sorry but I don't know what else to try.

---

### Post by trinimoses on 2011-05-29
i can copy some of the files.. still cant copy all..

any other ideas ?

---

### Post by silkworm2.5 on 2011-05-29
What happens? Do you get any error messages?

---

### Post by trinimoses on 2011-05-29
Just the standard permission error "Error while copying ... the folder dspam cannot be handled because you do not have permissions to read it"

hrm

---

### Post by silkworm2.5 on 2011-05-29
Odd. As far as I know, Root should be able to override the permissions. Try selecting the files, right clicking them, going into properties, and change the permissions to allow root access to read and write.

---

### Post by trinimoses on 2011-05-29
hrm... thats interesting.. i cant change the permission via the gui :(

---

### Post by silkworm2.5 on 2011-05-29
Are you sure that you are using the file browser window that opened from the terminal command I gave you? Because if that's no good, then I don't know what else to tell you... Are the unmoveable files encrypted or anything?
Actually, I just thought of another option. I am not familiar with centOS, but can you run that off a live system like Ubuntu? that might have better luck with the permissions.

---

### Post by trinimoses on 2011-05-29
the centos live disk fails to even load..

will play around and see what i can do..

thanks for the help

---

### Post by silkworm2.5 on 2011-05-29
The live disk fails to load? How did you install the system?

---

### Post by trinimoses on 2011-05-29
redownloading the live disk.. i think the one i have might be bad...

backj at it :(

---

