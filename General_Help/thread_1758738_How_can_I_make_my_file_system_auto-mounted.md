---
title: "How can I make my file system auto-mounted?"
date: 2011-05-15
forum: General Help
---

### Post by yinglcs2 on 2011-05-15
Hi,

Under my 'Places' in my file manager, I have a '21 GB file system'
How can I
1. Have that 21 GB auto mounted every time I login? I now need to right click and select 'mount'?

2. Give it a name so that it won't call 'a9f28af4-71db-4e49-8c05-f652bf808cc1/' under my directory '/media/'?

Thank you.

---

### Post by enimeizoo on 2011-05-15
You need to edit your /etc/fstab file. Since I din't know anything about your partition I can't help a lot more. 

The ntfs-config package can help you edit your fstab if your partition is ntfs.

If you want more details, please send the result of the folowing command :
```
sudo fdisk -l
```

---

### Post by Hedgehog1 on 2011-05-15
> **yinglcs2 said:**
> Hi,

Under my 'Places' in my file manager, I have a '21 GB file system'
How can I
1. Have that 21 GB auto mounted every time I login? I now need to right click and select 'mount'?

2. Give it a name so that it won't call 'a9f28af4-71db-4e49-8c05-f652bf808cc1/' under my directory '/media/'?

Thank you.

Lets say you want to call it 'hedgehog'.

First, you need to create a directory in the /media file of that same name:

```
sudo mkdir /media/hedgehog
```

Next, you edit your /etc/fstab (**F**ile **S**ystem **TAB**le)

```
gksudo gedit /etc/fstab
```

And add this line at the bottom of the file:

```
UUID=a9f28af4-71db-4e49-8c05-f652bf808cc1 /media/hedgehog  ext4    defaults   0  2
```

(please note - you may need to use ext3 instead of ext4)

Save the /etc/fstab, exit the text editor and reboot.

***The Hedge***

:KS

p.s. please substitute the name you prefer for '/media/hedgehog'.  '/media/hamster' is a good choice.  So is '/media/gerbil' :D

---

