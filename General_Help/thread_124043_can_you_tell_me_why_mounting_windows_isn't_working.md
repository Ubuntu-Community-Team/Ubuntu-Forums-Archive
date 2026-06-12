---
title: "can you tell me why mounting windows isn't working?"
date: 2006-01-31
forum: General Help
---

### Post by ice60 on 2006-01-31
hi, i know i'm an idiot - i'm trying to get my printer working and mount a windows partition at the same time 8-[ 

i'm trying to mount /dev/hda5 which is a partition in XP - the E drive. i have XP mounted in media already, it automatically mounts at boot  like this /media/windows 

so i made /media/windows2 for the E partition to be mounted from.

i then did this command
```
 sudo mount -t ntfs /dev/hda5 /media/windows2
```

and i got an error saying it couldn't be displayed. have i done something wrong? thanks.

---

### Post by carlosqueso on 2006-01-31
it's probably better to change your fstab file.

go into a terminal, type ```
sudo gedit /etc/fstab
```

and add this line to the bottom: ```
/dev/hda5 /media/windows2 ntfs umask=0222
``` then type ```
sudo mount -a 
``` in a terminal and it should work.

EDIT: it'll also mount automatically at boot.

---

### Post by hillbilly on 2006-01-31
I usually create a Win directory and mount under /mnt

> sudo mount -t ntfs /dev/hda5 /media/win

---

### Post by ice60 on 2006-01-31
thanks, carlosqueso and hillbilly :) i think i'll try and make it mount automatically. the error i was getting was a permissions problem. but, i'm going to try the automatic way instead.

i just opened fstab, does it matter the way you said 
```
/dev/hda5 /media/windows2 ntfs umask=0222
```
is slightly different to the way it would be if i made it how i have XP's partition mounted?
```
/dev/hda5       /media/windows2  ntfs    nls=utf8,umask=0222 0       0
```

---

### Post by carlosqueso on 2006-01-31
nope...that should work.  I'm just lazy and used spaces since tabs aren't friendly to this forum.

---

### Post by ice60 on 2006-02-07
[QUOTE=carlosqueso]nope...that should work.  I'm just lazy and used spaces since tabs aren't friendly to this forum.[/QUOTE]
thanks for the help :cool:

---

