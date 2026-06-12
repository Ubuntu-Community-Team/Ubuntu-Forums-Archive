---
title: "Help: Why don't I have permission to access my own external hard drive???"
date: 2010-12-13
forum: General Help
---

### Post by zhaotianwu on 2010-12-13
I've encountered a very frustrating problem. I have both my desktop and my laptop computer installed with Ubuntu 10.10 recently. And I use a external hard drive formatted in EXT3 as a backup. I created the EXT3 partition on my external hard drive using my laptop, but I cannot access those files using my desktop. What's going on? If one day I lost my laptop, does it mean even if I have backup, I can never access without my laptop??? How can I solve this problem? Thanks.

---

### Post by mick222 on 2010-12-13
On your laptop right click on the drive and set permissions to allow access  by others .

---

### Post by zhaotianwu on 2010-12-13
> **mick222 said:**
> On your laptop right click on the drive and set permissions to allow access  by others .

I tried right click but there is no such option, could you please give me a step by step description? Thanks.
By the way, if I format it into NTFS, will it solve this problem quickly? Now I'm using EXT3.

---

### Post by tajiknomi on 2010-12-13
> **zhaotianwu said:**
> I tried right click but there is no such option, could you please give me a step by step description? Thanks.
By the way, if I format it into NTFS, will it solve this problem quickly? Now I'm using EXT3.

[SIZE=2]Open up File-manager which has root-privileges using laptop[/SIZE]

```
[SIZE=3]***gksudo nautilus***[/SIZE]
```

[SIZE=2]and Apply the describe method,which is Posted above..[/SIZE]

---

### Post by bikodog on 2010-12-13
you need to adjust your settings with chmod.

post the output of this:

```

ls -l /media

```

---

### Post by zhaotianwu on 2010-12-13
> **tajiknomi said:**
> [SIZE=2]Open up File-manager which has root-privileges using laptop[/SIZE]

```
[SIZE=3]***gksudo nautilus***[/SIZE]
```[SIZE=2]and Apply the describe method,which is Posted above..[/SIZE]


Oh my god, I didn't expect it to be soooo complicated. Maybe I should reformat it as NTFS? Any cons about doing this?

---

### Post by lrgmmc on 2010-12-13
it realy is not that complicated. open terminal and run ```
ls -lh /media
``` then paste the result here.

---

### Post by zhaotianwu on 2010-12-13
> **lrgmmc said:**
> it realy is not that complicated. open terminal and run ```
ls -lh /media
``` then paste the result here.

Hi lrgmmc I don't understand what it does, but followed your instruction and here is the result:
drwxr-xr-x 2 root             root             4.0K 2010-11-22 08:48 cdrom
drwx------ 1 tianwuzhao tianwuzhao  4.0K 2010-12-12 15:20 Windows System

So?

---

### Post by zhaotianwu on 2010-12-13
Oh by the way, should I first plug in my external backup drive and then type in what you instruct here? I'm a little puzzled what I'm doing.

---

### Post by Krytarik on 2010-12-13
Connect the external drive first. Then try to access the drive as root, which should work: press Alt+F2 and enter "gksudo nautilus".

Most probably you have to make an entry for your backup-drive in the file "/etc/fstab". You get a good clue about what options you have to add to the entry by looking at the content of the file "/etc/mtab", after you have successfully accessed it with root-rights. You may post it here as well, if so, please add the content of the file "/etc/fstab".
EDIT: Please enclose the contents in code-tags (#) if you post them.

manual of fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You should also make you familiar with the "mount"-command: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

---

### Post by tgm4883 on 2010-12-13
> **Krytarik said:**
> Connect the external drive first. Then try to access the drive as root, which should work: press Alt+F2 and enter "gksudo nautilus".

Most probably you have to make an entry for your backup-drive in the file "/etc/fstab". You get a good clue about what options you have to add to the entry by looking at the content of the file "/etc/mtab", after you have successfully accessed it with root-rights. You may post it here as well, if so, please add the content of the file "/etc/fstab".
EDIT: Please enclose the contents in code-tags (#) if you post them.

manual of fstab: [https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)

You should also make you familiar with the "mount"-command: [https://help.ubuntu.com/community/Mount](https://help.ubuntu.com/community/Mount)

I wouldn't put it in fstab. If the drive is unmounted that will cause issues if the machine is rebooted.

The OP has a few options: 

[LIST=1]
[*]set the files to be accessible by other users
[*]use a different filesystem that doesn't keep permissions that linux cares about (ntfs/fat. I'm not sure if this would work as the files may be owned by root when mounted0
[*]Set the users/groups on both the desktop and laptop to have the same UID/GID (this one is the most difficult)
[/LIST]

---

### Post by Krytarik on 2010-12-13
> **tgm4883 said:**
> I wouldn't put it in fstab. If the drive is unmounted that will cause issues if the machine is rebooted.

The OP has a few options: 

[LIST=1]
[*]set the files to be accessible by other users
[*]use a different filesystem that doesn't keep permissions that linux cares about (ntfs/fat. I'm not sure if this would work as the files may be owned by root when mounted0
[*]Set the users/groups on both the desktop and laptop to have the same UID/GID (this one is the most difficult)
[/LIST]

Ok, I've only experience with mounting NTFS/FAT-partitions/drives. There are apparently other options, and permissions to take care of, when mounting ext-partitions/drives, sorry!

---

