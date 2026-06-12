---
title: "Auto-mount NTFS partitions"
date: 2010-03-14
forum: General Help
---

### Post by Ibrahim mufeed on 2010-03-14
Hi all,

On my laptop I have Windows and Ubuntu, and I use Ubuntu very often. How can I auto-mount the NTFS partitions once I run my Ubuntu without the need to manually ask to mount it and confirm with the root password each time and for each partition?

Regards,

---

### Post by louieb on 2010-03-14
You create an entry in file **/etc/fstab** - heres how [How to fstab - Ubuntu Forums]("http://ubuntuforums.org/showthread.php?t=283131")

---

### Post by DawieS on 2010-03-15
If you are running Karmic (Ubuntu 9.10) this will **not** help.

For a detailed solution, see [**_this_**]("http://ubuntuforums.org/showthread.php?t=1429790") thread.:grin::grin:

---

### Post by karthick87 on 2010-03-15
Install storage device manager it will help you..


```
sudo apt-get install pysdm
```

---

### Post by kazakore on 2010-03-15
> **DawieS said:**
> If you are running Karmic (Ubuntu 9.10) this will **not** help.

For a detailed solution, see [**_this_**]("http://ubuntuforums.org/showthread.php?t=1429790") thread.:grin::grin:
I have it working fine with 9.10. I do only have a single drive though, but as sdx/hdx drive letter is allocated dynamically is this not always the case?

If you only have one drive, and hence it will always come up as sda, then it should be easy. Recently bumped thread in this forum should help (or search my posts, called something like XP & 9.10)

---

### Post by Morbius1 on 2010-03-15
I will use the following as a kind of template to show how this was done in the olden days  ;).

***STEP 1: Find out how the system sees your partitions***

Open **Terminal**
Type **sudo blkid -c /dev/null**

This will output , among other things the following partition that I want to mount at boot:

>  [COLOR=Blue]/dev/sda1[/COLOR]: UUID="DA9056C19056A3B3" LABEL="WinXP" TYPE="ntfs"***STEP 2: Create a mount point for your partition to live in***

Open **Terminal**
Type **sudo mkdir [COLOR=DarkGreen]/media/Windows[/COLOR]**

*** STEP 3: Add a line in /etc/fstab/ to have this partition mount at boot:***

```
[COLOR=Blue]/dev/sda1[/COLOR] [COLOR=DarkGreen]/media/Windows[/COLOR]    ntfs    defaults,nls=utf8,umask=007,uid=1000,gid=46    0    0
```***Step 4: Mount the partition***

Open **Terminal**
Type [B]sudo mount -a

umask=007 [/B]will allow read /write access to owner and group and no one else.[B]
uid=1000 [/B]is you**. **It will make you the owner of the mount point.[COLOR=Blue] *To make sure 1000 is the right uid for you type** id** in a terminal*[/COLOR][B]
gid=46 [/B]is a group identifier. 46 is plugdev and every local login user is a member of the plugdev group so all local login users will have access.

---

