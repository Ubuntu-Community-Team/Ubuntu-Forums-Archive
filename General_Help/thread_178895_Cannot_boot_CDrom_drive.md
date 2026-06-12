---
title: "Cannot boot CDrom drive"
date: 2006-05-18
forum: General Help
---

### Post by spamzilla on 2006-05-18
When I try to run any CD, I get a message which says:

Boot unmounted

How do I remount this drive?

Thanks

---

### Post by spamzilla on 2006-05-19
Anyone? :(

---

### Post by depu on 2006-05-19
to mount the cd
sudo mount /media/cdrom0/

to unmount
sudo umount /media/cdrom0/

if that doesnt work simply replace cdrom0 by cdrom and try

---

### Post by spamzilla on 2006-05-20
When I do that I get a message saying :

mount:block device /dev/hdc is write pritected, mounting read only
mount:not in directory

How do I fix this?

I also tried /media/cdrom0 and got the same results...

---

### Post by Ramses de Norre on 2006-05-20
```
sudo mkdir /media/cdrom
sudo mount /dev/hdc /media/cdrom -t udf,iso9660 -o user,noauto
```

---

### Post by spamzilla on 2006-05-20
When I type in "sudo mkdir /media/cdrom" I get another message saying

mkdir: cannot create directory '/media/cdrom': File exists.

The same happens when i type in /cdrom0 instead of /cdrom. 

Then when I type in 

"sudo mount /dev/hdc /media/cdrom -t udf,iso9660 -o user,noauto" 

I get told that the block device /dec/hdc is write protected.

Does anyone know why this is happening?

Cheers

---

### Post by spamzilla on 2006-05-20
Anyone?

---

### Post by depu on 2006-05-20
[QUOTE=spamzilla]Then when I type in 

"sudo mount /dev/hdc /media/cdrom -t udf,iso9660 -o user,noauto" 

I get told that the block device /dec/hdc is write protected.

Does anyone know why this is happening?

Cheers[/QUOTE]
well i suppose if it is a cd ROM then u cant write into it anyways
but try 
cd /media/cdrom
to check if the cd is mounted or not

---

### Post by spamzilla on 2006-05-21
[QUOTE=depu]well i suppose if it is a cd ROM then u cant write into it anyways
but try 
cd /media/cdrom
to check if the cd is mounted or not[/QUOTE]

When I do that, the output says nothing about the cdrom at all :(

---

