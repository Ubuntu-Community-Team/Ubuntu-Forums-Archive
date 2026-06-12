---
title: "Use umask for ext3 partitions?"
date: 2006-06-16
forum: General Help
---

### Post by JohanSwe on 2006-06-16
I want to have a shared partition on my computer for all users. But if a user move a file there the other users don't have access to that file.

What I have read umask would be the soulution. I have tried to use in fstab like this:
```
/dev/hda4       /media/lagring  ext2    defaults[COLOR="red"],umask=000[/COLOR]          0       0
```
but then I can't even mount the partition. 

Can I use umask for ext2 and ext3 partitions and if so, what am I doing wrong? :sad: :?:

---

### Post by aysiu on 2006-06-16
I don't believe you can use umask for Ext2 partitions. Maybe someone else can confirm that, though.

---

### Post by ayoli on 2006-06-16
yes i think so, but group id is usable (ie: gid=1000) and should work, no ?

edit: seems not after a quick read of the mount man, but you can try to chown the partion to a grp which all your users belong to

---

### Post by JohanSwe on 2006-06-18
[QUOTE=ayoli]yes i think so, but group id is usable (ie: gid=1000) and should work, no ?

edit: seems not after a quick read of the mount man, but you can try to chown the partion to a grp which all your users belong to[/QUOTE]
Thanks, but how do I "chown the partion to a grp"? Can I do that in fstab?

[QUOTE=aysiu]I don't believe you can use umask for Ext2 partitions.[/QUOTE]
Sp what about Ext3?

---

### Post by aysiu on 2006-06-18
[QUOTE=JohanSwe]Sp what about Ext3?[/QUOTE]
I don't think umask works for Ext3 either.

---

### Post by JohanSwe on 2006-06-18
Wow, have never got a answer in seconds :D

---

### Post by JohanSwe on 2006-06-18
I'm still wondering how I can "chown the partion to a grp"? Can I do this in fstab?

---

### Post by ayoli on 2006-06-18
[QUOTE=JohanSwe]I'm still wondering how I can "chown the partion to a grp"? Can I do this in fstab?[/QUOTE]
no, i meant i have a partition mounted on /media/hda4 that belong to my first user, and my first user belong to group named 'users' and i add others users to this group, then they're able to browse my /media/hda4
since ubuntu create the first user with a group named same as username my /media/hda4 didn't belong to user group that why i did:
```
chown -R username.users /media/hda4
```

---

### Post by JohanSwe on 2006-06-18
Thanks ayoli. But what if one of the users move a file there from that user's home directory, will that file will be writeable by the other users then?

---

### Post by ayoli on 2006-06-18
yes, if this file is group-writable before move/copy
btw it's a crappy fix for your pb, there's must be a cleaner way to do that

---

### Post by JohanSwe on 2006-06-18
Yes, there's must be a cleaner way to do this. I would say this is something basic in an OS. 

It impossible to tell my mother and my siblings that they most edit permissions to share files. All they should have to so should be to move/copy the files to a shared directory that then would be writeable to the other users..

---

