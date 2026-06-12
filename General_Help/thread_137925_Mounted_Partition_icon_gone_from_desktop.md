---
title: "Mounted Partition icon gone from desktop"
date: 2006-02-28
forum: General Help
---

### Post by akniss on 2006-02-28
i recently installed the 686 kernel (updated from the 386).  no problems afterwards, except one annoying one.  I used to have an icon on my desktop for my FAT32 partition that i use to store files (its a dual boot system with XP).  The partition is mounted as /media/FileStore.  I can get the icon back by using the following command:
```
sudo invoke-rc.d dbus restart 
```

Question:  Why do I have to type this to get my icon back?  
Question:  How do I get the icon to show up automagically like it used to?

Yes, I have the volumes_visible checked in the GNOME configuration editor.

Contents of fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3       /media/FileStore vfat umask=000 0 0

```

---

### Post by DOtSlaSHuCantCME on 2006-02-28
[QUOTE=akniss]i recently installed the 686 kernel (updated from the 386).  no problems afterwards, except one annoying one.  I used to have an icon on my desktop for my FAT32 partition that i use to store files (its a dual boot system with XP).  The partition is mounted as /media/FileStore.  I can get the icon back by using the following command:
```
sudo invoke-rc.d dbus restart 
```

Question:  Why do I have to type this to get my icon back?  
Question:  How do I get the icon to show up automagically like it used to?

Yes, I have the volumes_visible checked in the GNOME configuration editor.

Contents of fstab:
```

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda5       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/hda3       /media/FileStore vfat umask=000 0 0

```[/QUOTE]



under "options"(for hda3) in fstab, instead of umask-000,put " defaults".
i would double check my mount references with Disk Manager 
and  in /Media.

---

### Post by DOtSlaSHuCantCME on 2006-03-01
[QUOTE=DOtSlaSHuCantCME]under "options"(for hda3) in fstab, instead of umask-000,put " defaults".
i would double check my mount references with Disk Manager 
and  in /Media.[/QUOTE]


for the difference of umask-000 and some more info :[http://www.ubuntuforums.org/showthread.php?t=137938](http://www.ubuntuforums.org/showthread.php?t=137938)

---

### Post by akniss on 2006-03-01
[QUOTE=DOtSlaSHuCantCME]for the difference of umask-000 and some more info :[http://www.ubuntuforums.org/showthread.php?t=137938](http://www.ubuntuforums.org/showthread.php?t=137938)[/QUOTE]


Nope.  That didn't change anything.  I still have to run ```
sudo invoke-rc.d dbus restart
``` to get the partition visible on the desktop or in the places menu.

Any other ideas???

---

### Post by akniss on 2006-03-02
BUMP.

Anyone?

---

### Post by pccampos on 2006-03-03
I'm having the same problem in dapper, a help would be appreciatted.

---

### Post by akniss on 2006-03-06
Nobody has any ideas, huh?  How about suggestions on other forums where I could look?  Anything?

---

### Post by akniss on 2006-03-13
So basically what i'm hearing [silence] is that I will have to type ```
sudo invoke-rc.d dbus restart
``` every time I start my laptop until Dapper comes out.  Which is going to be 6 weeks longer than originally scheduled...

---

### Post by frodon on 2006-03-16
Did you read this thread ? : [http://www.ubuntuforums.org/showthread.php?t=138267](http://www.ubuntuforums.org/showthread.php?t=138267)

It could work even if you don't use drapper.

---

### Post by akniss on 2006-03-16
[QUOTE=frodon]Did you read this thread ? : [http://www.ubuntuforums.org/showthread.php?t=138267](http://www.ubuntuforums.org/showthread.php?t=138267)

It could work even if you don't use drapper.[/QUOTE]

Thanks for the response.  That was one of the first things I checked.  From my first post:
[QUOTE=akniss]Yes, I have the volumes_visible checked in the GNOME configuration editor.[/QUOTE]

I lost my icons after an update... not sure why I seem to be the only one having this problem on Breezy.  Very frustrating.

---

### Post by frodon on 2006-03-16
I have quite the same problem, i have 2 data partitions and i'm only able to get the icon for the FAT32 one, i don't know why it doesn't work for my ext3 partition.
Anyway if i find a solution i will post it here (i didn't get the time to solve the problem yet).

---

