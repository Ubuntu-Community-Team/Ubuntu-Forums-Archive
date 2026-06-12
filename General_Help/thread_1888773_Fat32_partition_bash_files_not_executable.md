---
title: "Fat32 partition bash files not executable"
date: 2011-11-30
forum: General Help
---

### Post by rng on 2011-11-30
I have a bash script file on a fat32 partition. Earlier, I had used the command 'sudo chmod +x filename.sh' to make it executable and was able to execute it. I recently installed xfce and lxde desktops to check them. After that, I am not able to execute the bash script file as it is no more executable. The command 'sudo chmod +x filename.sh' runs without any comment or error message but file is not made executable (as seen by 'ls -l' command). Why has this occurred and how can I correct this? 

Thanks for your help.

Edit: The properties of this partition 'cannot be determined'.

---

### Post by coffeecat on 2011-11-30
FAT32 is a Microsoft filesystem and does not support Linux permissions, so neither chmod nor chown has any effect on a file saved to FAT32 or NTFS. You can change mount options in order to change permissions, in this case using the "exec" option, but that will have the effect of making all files on that partition executable.

Easiest solution is always to run bash scripts and binaries from Linux filesystems, and use FAT32 and NTFS only to store files.

---

### Post by rng on 2011-11-30
The 'mount' command shows that the partition is mounted with following options: 

```
/dev/sda6 on /media/fatpartition type vfat (rw,nosuid,nodev,uhelper=udisks,uid=1000,gid=1000,shortname=mixed,dmask=0077,utf8=1,showexec,flush)

```

How do I change this so that I can execute files from this partition? (It used to occur automatically earlier in my ubuntu installation, but has got disturbed after I tried xfce4 and lxde desktops and their file managers).

---

### Post by coffeecat on 2011-11-30
How are you mounting the partition, by means of /etc/fstab or simply by clicking on the partition in the Nautilus file browser? The best way would be to have a custom /etc/fstab line which includes the exec option, but as said before, this will make everything on the partition executable.

---

### Post by rng on 2011-11-30
I am mounting by simply choosing it from 'Places' menu of the top bar and I would like it to be like it only. Why is ubuntu mounting it with different options now? Can this be corrected? I don't mind all the files to be executable but I want to keep some scripts there only.

---

### Post by coffeecat on 2011-11-30
As to why, I'm not 100% sure or when it happened, but automounting with the exec option used to be the default but caused a lot of complaints because every time you double-clicked on a text file to open it with a text editor, the system asked you whether you wanted to run it.

You'll need a custom /etc/fstab entry. Here's a useful link. Post back if you need any help with that.

[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

---

### Post by mcduck on 2011-11-30
As far as I know the reason for the change was security, all files shouldn't be executable by default, that pretty much ruins the security benefits of having such thing as execute permission in the first place.

(I doubt the question about execute versus view when clicking the file had much to do with it, considering it's so easy to change that setting from Nautilus preferences and changing the default setting for that option would have been easier solution to the problem than changing the default mount options is.)

---

### Post by rng on 2011-11-30
How can I set system to automount with default option? 
And what would be a simple fstab entry for a fat32 partition (sda6) mounting to /media/fatpartition  ?

---

