---
title: "mount a hard drive?"
date: 2011-02-15
forum: General Help
---

### Post by r3dempt1on on 2011-02-15
hello everyone!

i recently decided to turn an old PC into an ubuntu server.

however i have two hard drives partitioned as so:
HD one:
1-ext4
2- swap
3- NTFS with files on it

HD two:
1- NTFS with files on it

i am having issues mounting the drives (specifically the NTFS partitions). i've googled the hell out of it and have come up with nothing

so my question is how do i mount the NTFS partitions? and furthermore, how do i add these partitions to samba?

thanks!
R3dempt1on

---

### Post by ahsan101 on 2011-02-15
> **r3dempt1on said:**
> hello everyone!

i recently decided to turn an old PC into an ubuntu server.

however i have two hard drives partitioned as so:
HD one:
1-ext4
2- swap
3- NTFS with files on it

HD two:
1- NTFS with files on it

i am having issues mounting the drives (specifically the NTFS partitions). i've googled the hell out of it and have come up with nothing

so my question is how do i mount the NTFS partitions? and furthermore, how do i add these partitions to samba?

thanks!
R3dempt1on
What version of Ubuntu are you using? i have installed two hard drives same like you, i have ubuntu 10.10 and it mounts them automatically and shows them in [Computer] . Yes you can add those drives to samba share, you have to use the utility Gadmin Tools it has the built-in support for samba from where you can use the Samba Sharing utility to add more Drives/Folders.

---

### Post by r3dempt1on on 2011-02-15
> **ahsan101 said:**
> What version of Ubuntu are you using? i have installed two hard drives same like you, i have ubuntu 10.10 and it mounts them automatically and shows them in [Computer] . Yes you can add those drives to samba share, you have to use the utility Gadmin Tools it has the built-in support for samba from where you can use the Samba Sharing utility to add more Drives/Folders.

oh sorry i'm running ubuntu server 10.10
so no GUI just shell

---

### Post by ahsan101 on 2011-02-15
> **r3dempt1on said:**
> oh sorry i'm running ubuntu server 10.10
so no GUI just shell
Ohh... Then it must be under /media , it would be mounted there.

---

### Post by r3dempt1on on 2011-02-15
all that shows up under /media is cdrom

when i $cd /dev
the drives show up

then i try $mount -t NTFS /dev/sda /media/sda
and it says the mount point does not exist
this is where i hit the brick wall.

---

### Post by ahsan101 on 2011-02-15
> **r3dempt1on said:**
> all that shows up under /media is cdrom

when i $cd /dev
the drives show up

then i try $mount -t NTFS /dev/sda /media/sda
and it says the mount point does not exist
this is where i hit the brick wall.
Look here [http://ubuntuforums.org/showthread.php?t=353487](http://ubuntuforums.org/showthread.php?t=353487)

---

### Post by r3dempt1on on 2011-02-15
awesome i have the drives mounted !

but could you elaborate as to how to add files to samba using shell?

i appreciate the help

---

### Post by ahsan101 on 2011-02-15
> **r3dempt1on said:**
> awesome i have the drives mounted !

but could you elaborate as to how to add files to samba using shell?

i appreciate the help
Though i never experienced samba still i have some information about it probably it was in smb.conf , look here [http://www.lexinformatica.org/index.php/term/,9da4ab975b5460a0ad52595a92aca352925e565e6facad5caa9b6eb0aa5960ac61946d5452afb0a0ac52585756aa9c63a25361a05e649a5e9d566163549ca1a0b16f5960929da958666e525853a56466a26d52a070b0a453aa.xhtml](http://www.lexinformatica.org/index.php/term/,9da4ab975b5460a0ad52595a92aca352925e565e6facad5caa9b6eb0aa5960ac61946d5452afb0a0ac52585756aa9c63a25361a05e649a5e9d566163549ca1a0b16f5960929da958666e525853a56466a26d52a070b0a453aa.xhtml) . Hope it helps.

---

### Post by r3dempt1on on 2011-02-15
perfect thanks!!

---

### Post by ahsan101 on 2011-02-15
> **r3dempt1on said:**
> perfect thanks!!
Welcome :)

---

