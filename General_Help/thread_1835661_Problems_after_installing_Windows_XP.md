---
title: "Problems after installing Windows XP"
date: 2011-08-29
forum: General Help
---

### Post by Nostigex on 2011-08-29
[LEFT][LEFT]Today I installed Windows XP on the same hard drive as my Ubuntu installation (10.04.2). Windows XP is on sda4 and Ubuntu on sda1. Windows XP overrode Ubuntu, so I had to reinstall something called GRUB2. I did so using the instructions [here]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB2") (under the 'Copy LiveCD Files' method).

Upon choosing Ubuntu from the boot menu, I encounter some weird errors amidst a lot of text... these seem to be key lines:

> 
An error occurred while mounting 0
An error occurred while mounting /media/Swap
Press S to skip mounting or M for manual recoveryWhen I reach the desktop, my wallpaper isn't there anymore, and there are a bunch of little things not working - can't right click on the desktop, shortcuts don't work, Dropbox doesn't recognize its folder, etc.

Now, I know that /media/Swap is an extended partition, sda2, containing my swap file on sda5. I don't know what "0" is. Sda2 doesn't show up in Storage Device Manager. What's more, I noticed that Storage Device Manager seems to be confusing sd**b**2 (my Movies partition, on a separate hard drive) with my root drive. For example, if I change the name of sdb2 to "Movies", sda1 (which is my root partition) renames itself to "Movies"!

In threads with similar problems, people are often asking for the contents of the fstab file, which I assume has to do with bootup. So here it is:

```

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc  nodev,noexec,nosuid               0  0  
# / was on /dev/sda1 during installation
UUID=2a0dab88-e2f0-4285-81d9-5c86cccffc8d  /               ext4  errors=remount-ro                 0  1  
# swap was on /dev/sda5 during installation
UUID=4934ac2e-f33c-48e9-8119-b2ab1a5fbfb7  none            swap  sw                                0  0  
/dev/fd0                                   /media/floppy0  auto  rw,user,noauto,exec,utf8          0  0  
/dev/sda2                                  /media/Swap     ext4  
defaults                          0  0  
/dev/sdb2                                  /media/Movies   ext4  defaults                          0  0  
/dev/sda3                                  /media/Storage  ext4  defaults                          0  0  
/dev/sda4                                  /media/Windows  ntfs  nls=iso8859-1,ro,users,umask=000  0  0  

```Also, the results of "blkid":

```

/dev/sda1: UUID="2a0dab88-e2f0-4285-81d9-5c86cccffc8d" TYPE="ext4" 
/dev/sda3: LABEL="Storage" UUID="0097d2f9-c2df-4d5d-93cc-3e45f8edaace" TYPE="ext4" 
/dev/sda4: LABEL="Windows" UUID="9A5437AB54378951" TYPE="ntfs" 
/dev/sda5: UUID="4934ac2e-f33c-48e9-8119-b2ab1a5fbfb7" TYPE="swap" 
/dev/sdb2: LABEL="Movies" UUID="e083a6eb-fcd6-4771-bf30-a62b8afee3ec" TYPE="ext4" 

```And the results of "sudo fdisk -l":

```
Disk /dev/sda: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000905bb

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        4985    40039062+  83  Linux
/dev/sda2            4985        5484     4008961    5  Extended
/dev/sda3            5485       24664   154063350   83  Linux
/dev/sda4   *       24665       30400    46074420    7  HPFS/NTFS
/dev/sda5            4985        5484     4008960   82  Linux swap / Solaris

Disk /dev/sdb: 100.3 GB, 100256292864 bytes
255 heads, 63 sectors/track, 12188 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00091150

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb2               1       12189    97904640   83  Linux

```Can anyone help me with this mess?

[/LEFT]
[/LEFT]

---

### Post by JC Cheloven on 2011-08-29
Hi, the info you provided is in fact relevant. The problem is weird though.

First, to clarify, it seems sda2 is the extended partition, and that your swap is in the logical partition sda5. The extended partition is not reported by blkid (normal behaviour). Please see the output of this if you want to confirm sda2 as the extended partition: ```
sudo fdisk -l
```  
Note: sda2 being the extended partition is a bit unusual, but possible anyway I think.

Other than that, I'm addmitedly a bit confused (== out of ideas) about the state you report, which boots but with lots of small things not working. I only devise at this moment something that is a bit unlikely to solve your problem, but that you can try for cheap:  
Mounting devices by UUID is supposed to be more secure, but I've found in practice quite some problems with that, which were solved by simply mounting by device name. So please open a terminal and let's try:

- First of all, please make a backup of your fstab file, just in case. Type ```
sudo cp /etc/fstab /etc/fstabBAK
```

- Now edit your fstab file. I'll use the command-line editor 'nano' here but you can edit by other means if you want. Please type ```
sudo nano /etc/fstab
```
now please replace [COLOR="Red"]UUID=2a0dab88-e2f0-4285-81d9-5c86cccffc8d[/COLOR]
with [COLOR="Red"]/dev/sda1[/COLOR]
and replace [COLOR="Red"]UUID=4934ac2e-f33c-48e9-8119-b2ab1a5fbfb7[/COLOR]
with [COLOR="Red"]/dev/sda5[/COLOR]
Do Ctrl-O to save, and Ctrl-X to exit. 

Reboot and let's see if it helped. 
If not, to revert the changes, please open again a terminal and do
```
sudo mv /etc/fstab /etc/fstabRUBBISH
sudo cp /etc/fstabBAK /etc/fstab

```
... or simply re-edit the fstab file to revert it to its original state (you have in this thread the contents of the file to see).

---

### Post by Nostigex on 2011-08-29
Thanks for the response. I tried your suggestion of mounting sda1 and sda5 by device name instead of UUID, but it didn't work. I posted the output of "sudo fdisk -l" in my original post.

---

### Post by scott_g on 2011-08-29
Is your wallpaper a non-standard one (ie: is it a home photo or something?)?  If so, what drive is it located on?

---

