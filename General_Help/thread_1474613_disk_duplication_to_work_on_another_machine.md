---
title: "disk duplication to work on another machine"
date: 2010-05-06
forum: General Help
---

### Post by sdowney717 on 2010-05-06
cant I simply take a working ubuntu hard drive and dd copy it onto another disk. Then put the disk in the other pc and it will work?

This way I could configure a machine at home, take the disk with me and use it at a place with no internet access.

---

### Post by john newbuntu on 2010-05-06
I haven't tried it.  I have a feeling it would work if the disks are same or if the second is bigger than the first.  But the curious part is the interpretation of partition information and disk geometry of the second drive.  Also, the sparseness of files are retained when you use dd - not a major issue.

---

### Post by DawieS on 2010-05-10
Recently I replaced an **IDE** disk in my kid's PC with a **SATA** disk. Since she has put a lot of time into customizing her Ubuntu installation, I decided to duplicate her installation onto the new disk, instead of going for a new install. What I did was:

1) Boot from another working installation, or Live CD, having both old (source) and new (target) disks connected.

2) Using **GParted**, prepare and format the new target disk with partitions similar in size or larger than the source. Also label the partitions for your own clarity. If you want to keep the source partition label, rather rename the source partition to something else like 'Source', and label the target partition to the same original source name.

3) Using **GParted**, check that the target boot partition has a boot flag, also right-click on the partition > Information, copy/paste the **UUID** into a text file (you will need that later).

4) Open a file browser and click on both the source and target partitions to mount them. Click on **File System**, then on **/media** to check that they are mounted there.

(For this example let's assume the source partition is labeled as [COLOR=Black]**Source**[/COLOR], and the target partition labeled as [COLOR=Black]**Target**[/COLOR], please use your own labels instead)

Open a terminal. Change the current working directory to the target.
```
cd /media/Target
```Print working directory, to double check that you are in the correct folder.
```
pwd
```5) Copy all files/folders from the source.
```
sudo cp /media/Source/* . -p -r
```(The wild character '*' nominates everything in the source folder)
(The 'dot' keeps the same name)
(The -p preserves file/folder attributes (permissions, dates, etc))
(The -r copies directories recursively)

6) After the copy, rectify the partition **UUID** on the target partition by editing 2 files:
```
sudo gedit /media/Target/etc/fstab
```Replace the UUID of the boot partition with the one you pasted into a text file earlier. If you use a different type of file system in the new partition, also rectify that, and save.
```
sudo gedit /media/Target/boot/grub/grub.cfg
```Replace all occurrences of the source partition **UUID**, with the target partition **UUID**, using the **Search/Replace** function, and save.

7) Install the new drive in the final configuration and adjust the BIOS boot sequence. Boot up, open a terminal, and enter:
```
sudo update-grub
```This will update the grub menu in the new configuration with other partition UUID's that may also have changed.
:smile::razz::smile:

---

### Post by john newbuntu on 2010-05-10
@DawieS, Thanks for sharing that information.  The interesting thing in your note is that I did not see any changes made to the MBR or to the DOS compat region.  Unless you did a grub-install from a liveCD, I am not sure on how grub worked to boot the system.

---

### Post by Ocxic on 2010-05-10
Yes a dd copy of a disk will work, the UUID of the filesystems should stay the same, if not you can udate the /etc/fstab with the new values with  "blkid" from an live cd.

---

### Post by The Real Dave on 2010-05-10
The easiest way to do what you want to achieve is to simply to a full disk-disk copy with [Clonezilla]("http://www.clonezilla.org/"). Grab the ISO, burn it off and boot it up :) It's then quite simple to follow the instructions and copy one disk, or partition to another, or to make an image of it for backup purposes. Just be sure on which drive is being copied to where :)

---

### Post by dino99 on 2010-05-10
> **The Real Dave said:**
> The easiest way to do what you want to achieve is to simply to a full disk-disk copy with [Clonezilla]("http://www.clonezilla.org/"). Grab the ISO, burn it off and boot it up :) It's then quite simple to follow the instructions and copy one disk, or partition to another, or to make an image of it for backup purposes. Just be sure on which drive is being copied to where :)

yes keep it simple :P   21th century here

---

### Post by DawieS on 2010-05-10
> **john newbuntu said:**
> @DawieS, Thanks for sharing that information.  The interesting thing in your note is that I did not see any changes made to the MBR or to the DOS compat region.  Unless you did a grub-install from a liveCD, I am not sure on how grub worked to boot the system.
Thanks to **john newbuntu** for pointing that out. I have neglected to mention that the MBR of the disk I was using already contained a Grub bootloader from a previous Ubuntu installation.

I should point out that:
1) if you are using a brand new disk, or
2) the partition layout on the new disk is not similar to the old one, or
3) if you want a different boot loader on the new disk,
then a Grub (or Windows) bootloader should be installed on the new disk, instead of updating the grub.cfg file as under 6) in my previous post. The following tutorial by **talsemgeest** is easy to follow and use:
[**How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)**]("http://ubuntuforums.org/showthread.php?t=1014708")

Also many thanks to **Ocxic**, **The Real Dave** and **dino99** for that useful information! I will surely use that in future.

The merit of using the procedure outlined above, is really only demonstrated once you are stuck somewhere without Internet access, and only a Live CD at hand. By using a few basic Linux commands, you will still be able to clone drives and partitions.
:smile::razz::smile:

---

