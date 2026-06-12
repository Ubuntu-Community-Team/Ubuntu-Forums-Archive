---
title: "An error occured while mounting /media"
date: 2011-01-07
forum: General Help
---

### Post by Manie on 2011-01-07
:KS

Havent got a clue why this started to happen recently, it says press S to skip or M to fix manually, i always skip adn everything is just fine, just would like to know why im getting this message and how to get rid of it


BTW yes i googled and searched the forum, i couldnt find this exact message

---

### Post by cmoraes on 2011-01-07
Does /var/log/messages show any error?

---

### Post by dracayr on 2011-01-07
why do you have anything mounted on /media anyway? Flash drives and removable media are mounted on subdirectories of /media by default, mounting a drive on /media itself might not be a good idea.

---

### Post by Linyx on 2011-01-07
> **Manie said:**
> :KS

Havent got a clue why this started to happen recently, it says press S to skip or M to fix manually, i always skip adn everything is just fine, just would like to know why im getting this message and how to get rid of it


BTW yes i googled and searched the forum, i couldnt find this exact message

[SIZE=2]Have you edited FSTAB or tried some tool for Auto-mounting.....?

Post the output of

    [/SIZE]```
[SIZE=2]cat /etc/fstab[/SIZE]
```
[SIZE=2] 
Also 

    [/SIZE]```
[SIZE=2]sudo fdisk -l[/SIZE]
```

---

### Post by Manie on 2011-01-07
> **cmoraes said:**
> Does /var/log/messages show any error?

added the file in attachment

---

### Post by Manie on 2011-01-07
> **dracayr said:**
> why do you have anything mounted on /media anyway? Flash drives and removable media are mounted on subdirectories of /media by default, mounting a drive on /media itself might not be a good idea.
Ive never altered anything, i plug in my External, or open my Windows partition to get a file if i dont need to reboot,
> **Linyx said:**
> [SIZE=2]Have you edited FSTAB or tried some tool for Auto-mounting.....?

Post the output of

    [/SIZE]```
[SIZE=2]cat /etc/fstab[/SIZE]
```
[SIZE=2] 
Also 

    [/SIZE]```
[SIZE=2]sudo fdisk -l[/SIZE]
```

I've never edited that, dont even know what it is, but here goes


```
manie@manie-laptop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda5 during installation
UUID=0fd0524f-6d25-47f1-9bd8-a5efbb5ea7f9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda6 during installation
UUID=7ff816b5-ff34-411c-b0bf-5542b2cc9311 none            swap    sw              0       0
# DazukoFS ...
# Example of mounting one dir onto dazukofs (directory to be protected by AVIRA Guard)
#/home/shared /home/shared dazukofs
/media    /media    dazukofs
# ... DazukoFS

```


and


```
manie@manie-laptop:~$ sudo fdisk -l
[sudo] password for manie: 

Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0002173e

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       27725   222589952    7  HPFS/NTFS
/dev/sda3           27725       30402    21504001    5  Extended
/dev/sda5           27725       30285    20563968   83  Linux
/dev/sda6           30285       30402      939008   82  Linux swap / Solaris

```

---

### Post by Linyx on 2011-01-08
Remove this line from the fstab and try again....

```
/media    /media    dazukofs

```

---

### Post by Manie on 2011-01-08
> **Linyx said:**
> Remove this line from the fstab and try again....

```
/media    /media    dazukofs

```

How do i remove that line? i ran cat /etc/fstab in terminal

---

### Post by Linyx on 2011-01-08
> **Manie said:**
> How do i remove that line? i ran cat /etc/fstab in terminal

sudo gedit /etc/fstab

Gedit is an text-editor, their you can simple remove that line and save it....

---

### Post by WorMzy on 2011-01-08
> **Linyx said:**
> _gk_sudo gedit /etc/fstab

Fixed that for you. Don't use sudo for graphical applications, it can lead to permission problems.

OP: Any idea where that dazukofs line came from?

---

### Post by Manie on 2011-01-08
> **Linyx said:**
> sudo gedit /etc/fstab

Gedit is an text-editor, their you can simple remove that line and save it....
will reboot now to see if that helps
> **WorMzy said:**
> Fixed that for you. Don't use sudo for graphical applications, it can lead to permission problems.

OP: Any idea where that dazukofs line came from?
Was testing Avira and it was needed for it to run properly, but i have no use for it any more, it isnt as good as i thought for scanning my windows partition, but i'll remove it if its the reason.


EDIT: that did the job, thanks, topic solved:KS

---

### Post by pasxalis17 on 2011-09-15
I have aproximately the same error, I reinstalled windows and GRUB stopped working, to fix it I run boot repair from an ubuntu 10.10 live cd.
After that the known message appears but on /media/sda5, on sda5 is the file system.

 cat /etc/fstab gives me:
```
# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc        proc  nodev,noexec,nosuid                 0  0  
/dev/sda6                                  /            ext4  errors=remount-ro                   0  1  
# /boot was on /dev/sda7 during installation
UUID=f1e72a2d-e9c4-4d79-a4f0-fb50d5c92635  /boot        ext4  defaults                            0  2  
# swap was on /dev/sda8 during installation
UUID=5376ac70-46cb-41a8-bc26-c68929075f48  none         swap  sw                                  0  0  
/dev/sda5                                  /media/sda5  ntfs  nls=iso8859-1,users,umask=000,user  0  0  
```

and sudo fdisk -l gives me :
```
omitting empty partition (5)

Disk /dev/sda: 1000.2 GB, 1000204886016 bytes
255 heads, 63 sectors/track, 121601 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x1dd61dd5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       25496   204788736    7  HPFS/NTFS
/dev/sda2           25496      121601   771961857    5  Extended
/dev/sda3           35696      121601   690031616    7  HPFS/NTFS
/dev/sda5           25496       35236    78240768   83  Linux
/dev/sda6           35236       35261      194560   83  Linux
/dev/sda7           35261       35695     3490816   82  Linux swap / Solaris

```

What should I delete from fstab?

---

### Post by WorMzy on 2011-09-16
> sda5 is the filesystem

Which filesystem? fdisk is saying that it's a linux partition (e.g. ext4), but in fstab you've listed it's filesystem as ntfs. Did you mean to mount sda1 or sda3 instead?

You've also specified "users" and "user" in the options, you only need one of these.

user = anyone can mount the filesystem, but only the person that mounted it can unmount it.
users = anyone can mount or unmount the filesystem.

currently, "user" is in effect, because it comes after "users" in the list.

Those are the only problems I can see without seeing the output for ```
blkid
``` but I think the incorrect filesystem specified for sda5 is what's causing the problem.

---

