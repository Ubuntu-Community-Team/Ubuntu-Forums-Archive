---
title: "Problem with Automatic Mounting"
date: 2010-08-26
forum: General Help
---

### Post by alaukikyo on 2010-08-26
I used ntfs-config to make my ntfs partitions automatically mount at boot.Yesterday i Deleted my Windows Partiton using disk utility then after i booted up every time i got the message  "Press s to skip mounting and m for manual recovery" i installed pysdm and set the options of all ntfs partitions to default and renamed them to b,c,d now i have lot of problems with disks i can see only two drives and one is empty. 
Is there any way to restore all the partion settings to default.
here is the my partition information 
> Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x41854184

   Device Boot      Start         End      Blocks   Id  System
/dev/sda2            4463       38914   276729834+   f  W95 Ext'd (LBA)
/dev/sda5            4463       15935    92156841    7  HPFS/NTFS
/dev/sda6           15936       27408    92156841    7  HPFS/NTFS
/dev/sda7           27409       33194    46471482+   7  HPFS/NTFS
/dev/sda8           33194       38674    44016640   83  Linux
/dev/sda9           38674       38914     1926144   82  Linux swap / Solaris
and my fstab file
> 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda8 :
UUID=afae7a05-0866-4f22-86c9-22040bf5c066    /    ext4    errors=remount-ro    0    1
/dev/sda7    /media/Disk    ntfs-3g    defaults,noexec,nosuid,nodev,noauto,users,locale=en_IN    0    0
/dev/sda6    /media/New\040Volume_    ntfs-3g    defaults,noexec,nosuid,nodev,noauto,users,locale=en_IN    0    0
#Entry for /dev/sda5 :
UUID=463427F03427E1A3    /media/_    ntfs-3g    defaults    0    0
/dev/sda6    /media/__    ntfs-3g    defaults    0    0
/dev/sda7    /media/___    ntfs-3g    defaults    0    0
UUID=E8866489866459D8    /media/E8866489866459D8    ntfs-3g    defaults,nosuid,nodev,locale=en_IN    0    0
#Entry for /dev/sda9 :
UUID=a878a0b5-7d18-4c4b-bfe5-7671e290c4c1    none    swap    sw    0    0


---

### Post by alaukikyo on 2010-08-26
I fixed the problem By Resetting all the values to default and using ntfs-config to configure and rebooting.
BUt the problem of Showing "Press S to skip mounting and m for manual configuration" is still there i  beilive it will be solved after disabling automounting the patitions at boot and ten enabling it agian but i don't know a way to turn it off.If some of you can help:)

---

### Post by alaukikyo on 2010-08-28
BumP

---

### Post by Morbius1 on 2010-08-28
And you wonder why some people would like to see all these utilities to automount partitions purged from the repository. I mean what the heck is this:

[COLOR=Blue]/dev/sda6[/COLOR]    /media/New\040Volume_    ntfs-3g    defaults,noexec,nosuid,nodev,noauto,users,locale=e  n_IN    0    0
UUID=463427F03427E1A3    /media/_    ntfs-3g    defaults    0    0
[COLOR=Blue]/dev/sda6[/COLOR]    [COLOR=Orange]/media/__    [/COLOR]ntfs-3g    defaults    0    0
/dev/sda7[COLOR=Orange]    /media/___[/COLOR]    ntfs-3g    defaults    0    0

Pleas post the output of the following command so we can get some information about your partitions:
```
sudo blkid -c /dev/null
```And post your current fstab so we have the current status.

---

### Post by alaukikyo on 2010-08-29
Here the output
> 
/dev/sda5: LABEL="New Volume" UUID="463427F03427E1A3" TYPE="ntfs" 
/dev/sda6: LABEL="New Volume" UUID="36E42DAEE42D70F3" TYPE="ntfs" 
/dev/sda7: LABEL="Disk" UUID="868AC3F48AC3DF35" TYPE="ntfs" 
/dev/sda8: UUID="afae7a05-0866-4f22-86c9-22040bf5c066" TYPE="ext4" 
/dev/sda9: UUID="a878a0b5-7d18-4c4b-bfe5-7671e290c4c1" TYPE="swap" 

And Here is My fstab file
> 

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc	/proc	proc	nodev,noexec,nosuid	0	0
#Entry for /dev/sda8 :
UUID=afae7a05-0866-4f22-86c9-22040bf5c066	/	ext4	errors=remount-ro	0	1
/dev/sda7	/media/Disk	ntfs-3g	defaults,noexec,nosuid,nodev,noauto,users,locale=en_IN	0	0
/dev/sda6	/media/New\040Volume_	ntfs-3g	defaults,noexec,nosuid,nodev,noauto,users,locale=en_IN	0	0
#Entry for /dev/sda5 :
UUID=463427F03427E1A3	/media/_	ntfs-3g	defaults	0	0
/dev/sda6	/media/__	ntfs-3g	defaults	0	0
/dev/sda7	/media/___	ntfs-3g	defaults	0	0
UUID=E8866489866459D8	/media/E8866489866459D8	ntfs-3g	defaults,nosuid,nodev,locale=en_IN	0	0
#Entry for /dev/sda9 :
UUID=a878a0b5-7d18-4c4b-bfe5-7671e290c4c1	none	swap	sw	0	0


---

### Post by Morbius1 on 2010-08-29
This is going to be such a big change to your fstab that I would take the precaution of making a backup copy:
```
sudo cp -a /etc/fstab /etc/fstab.bak
```Make a new set up mountpoints:
```
sudo mkdir /media/Diska5
sudo mkdir /media/Diska6
sudo mkdir /media/Diska7
```Open fstab as root:
```
gksu gedit /etc/fstab
```Place a # in front of all the lines that reference ntfs so that they look like this:
> #/dev/sda7    /media/Disk    ntfs-3g    defaults,noexec,nosuid,nodev,noauto,users,locale=e  n_IN    0    0
#/dev/sda6    /media/New\040Volume_    ntfs-3g    #defaults,noexec,nosuid,nodev,noauto,users,locale=e  n_IN    0    0
#UUID=463427F03427E1A3    /media/_    ntfs-3g    defaults    0    0
#/dev/sda6    /media/__    ntfs-3g    defaults    0    0
#/dev/sda7    /media/___    ntfs-3g    defaults    0    0
#UUID=E8866489866459D8    /media/E8866489866459D8    ntfs-3g    defaults,nosuid,nodev,locale=en_IN    0    0Add new lines in fstab that look like this:
```
/dev/sda5 /media/Diska5 ntfs defaults,umask=000,locale=en_IN    0    0
/dev/sda6 /media/Diska6 ntfs defaults,umask=000,locale=en_IN    0    0
/dev/sda7 /media/Diska7 ntfs defaults,umask=000,locale=en_IN    0    0
```Save fstab, exit gedit, and back in the terminal issue the following command:
```
sudo mount -a
```If there are any errors after you run "sudo mount -a" report back. Otherwise see if you can access all your ntfs partitions at their new mounpoints.

---

### Post by alaukikyo on 2010-08-29
Cheers Will Try that out:D

---

### Post by alaukikyo on 2010-08-30
Thanks Everything went fine an my problem is fixed :)

---

