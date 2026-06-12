---
title: "Can't delete a folder - need permissions"
date: 2010-09-24
forum: General Help
---

### Post by fibrebiz on 2010-09-24
I have a 500GB iomega portable HD. I used Gparted to split the drive into two partitions, a fat32 of roughly 400GB and an EXT4 partition of roughly 100GB.

On my EXT4 partition, there is a folder called lost+found. I can't delete it because I need to be root, yet my account has administrator priviliges (but I CAN rename the folder). 
I can't create other folders on this partition, nor can I copy-paste and files on there either.

Basically, that partition is unuseable. In the properties of the folder, it says that I am not the owner so I cannot change the permissions. (It is definitely MY hard drive)
All options are greyed out.

How do I give myself permission to use this EXT4 partition?

---

### Post by nothingspecial on 2010-09-24
In a terminal

```
sudo chown -R username:username /path/to/partition
```

change both instances of username for your actual username

for example the path name might be /media/disk although these days it probably a random jumble of letters and numbers

---

### Post by rgiles43 on 2010-09-24
Hello,

You can use:

sudo chown root:root <file name or directory>


Hope this helps

---

### Post by fibrebiz on 2010-09-24
How do I find the path to the directory?

It seems to be /media/ext4  (I called the partition EXT4) but that doesn't work in terminal

---

### Post by fibrebiz on 2010-09-24
Actually, that terminal command seems to have worked, despite saying no such file or directory.

Thanks for the help

---

### Post by nothingspecial on 2010-09-24
> **fibrebiz said:**
> How do I find the path to the directory?

It seems to be /media/[COLOR=Red]ext4[/COLOR]  (I called the partition [COLOR=Red]EXT4[/COLOR]) but that doesn't work in terminal

It`s case sensetive

ext4 or EXT4?

```
mount
```

will list all your mounted partitions

---

### Post by rgiles43 on 2010-09-24
Hello,

I am no expert but I believe that you can change the owner for the disk by doing the following:

sudo chown -R username:usernamed /media/ext4


You can also determine your full path by typing pwd

Hope this helps

---

### Post by perspectoff on 2010-09-24
You can also use a file manager to do the job. Start a file manager with root privileges:

 sudo nautilus

or

 sudo dolphin

The file managers will also allow you to mount the disks automatically.

---

### Post by ajgreeny on 2010-09-24
> **perspectoff said:**
> You can also use a file manager to do the job. Start a file manager with root privileges:

 sudo nautilus

or

 sudo dolphin

The file managers will also allow you to mount the disks automatically.
```
gksudo nautilus
``` and ```
kdesu dolphin
``` please, or you could come unstuck.  See **Root sudo** in my signature for details

---

