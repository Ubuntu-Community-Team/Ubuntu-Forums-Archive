---
title: "My drives appear 2-times..."
date: 2010-12-15
forum: General Help
---

### Post by Linyx on 2010-12-15
[SIZE=2]I don't know why my drives appear ***two*** time's in My-Places....its not every time,but it shows some of My drives two time.....I Had attached a Screen-Shot of that...


Any Help will be appreciated[/SIZE]

Moreover , My FSTAB:-

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>

proc    /proc    proc    nodev,noexec,nosuid    0    0
#Entry for /dev/sda8 :
UUID=93a73f23-04a7-4ed2-afb9-bff7fffa66ca    /    ext3    errors=remount-ro    0    1
#Entry for /dev/sda6 :
UUID=32B4D35146D6CA5D    /media/Multimedia    ntfs    defaults,utf8,umask=007,uid=1000,gid=1000 0 1
#Entry for /dev/sda5 :
UUID=232D470307EF2C88    /media/My_Data    ntfs    defaults,utf8,umask=007,uid=1000,gid=1000 0 1
#Entry for /dev/sda7 :
UUID=31d375a6-05be-4873-a867-d6acb273ec89    none    swap    sw    0    0


```

Edit:- [SIZE=2]As you can guess from fstab, that i had Auto-mounted NTFS-drives.... I actually used*** NTFS-Configure tool***, however i had edited a line FOR read&Write,......[/SIZE]

---

### Post by Linyx on 2010-12-15
[SIZE="2"]Bump[/SIZE]

---

### Post by Linyx on 2010-12-15
[SIZE="2"]Only "My_Data" is Shown 2times in My Places menu,

help me to get out of this....[/SIZE]

---

### Post by mc4man on 2010-12-15
It's possible that a change to fstab options would resolve, but i forget what.

The other way is to use /dev/disk/by-uuid/xxxxx...  instead of UUID= for that drive.
Assuming your posted fstab is correct then something like this for /dev/sda5 
```
#Entry for /dev/sda5 :
/dev/disk/by-uuid/232D470307EF2C88    /media/My_Data    ntfs    defaults,utf8,umask=007,uid=1000,gid=1000 0 1


```
see here first, inc. links to bug report and another thread - in that thread examples in post 12, 14
[http://ubuntuforums.org/showthread.php?t=1561929](http://ubuntuforums.org/showthread.php?t=1561929)

---

### Post by Linyx on 2010-12-16
[SIZE=2]Worked nice...thanks :p...

But i don't know why this is Happen when only UUID is at the start of line...:confused:
[/SIZE]

---

