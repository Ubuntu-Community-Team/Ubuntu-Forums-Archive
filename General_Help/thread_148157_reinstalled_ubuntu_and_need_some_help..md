---
title: "reinstalled ubuntu and need some help."
date: 2006-03-21
forum: General Help
---

### Post by risknothin on 2006-03-21
Ok so i reinstalled and now everything is out of sorts.

The problem im having is with windows hard driveswhich are mounted but are only available for root and i tried to go in an change the permissions through the terminal and cant get it to work. 
 
also before i had it so i never had to enter a password except when i was accessing root. how do i get back to that?

Any suggestions?

---

### Post by manicka on 2006-03-21
If the windows drives/partitions are ntfs then writing to ntfs partitions is not supported. You can only write to fat32 partitions

---

### Post by risknothin on 2006-03-21
yeah but i cant even look at them, i dont care about writing to them just being able to see what is on them.  How can i do that?

---

### Post by manicka on 2006-03-21
can you post the contents of your /etc/fstab

---

### Post by manicka on 2006-03-21
[QUOTE=risknothin]
also before i had it so i never had to enter a password except when i was accessing root. how do i get back to that?
[/QUOTE]

This is the normal behaviour, what are you experiencing?

---

### Post by risknothin on 2006-03-21
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda4       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda2       /media/hda2     ntfs    defaults       0       0
/dev/hda5       /media/hda5     ntfs    defaults        0       0
/dev/hdb1       /media/hdb1     ext2    rw,defaults        0       2
/dev/hda6       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0


As to do with the passwords... Im a beginner and i had my whole ubuntu running just like i wanted it to but now i have to put passwords in all the time i want to remove that again.

---

### Post by manicka on 2006-03-21
Do you have folders inside /media called hda2 and hda5?

Passowrds. You should only be asked for a password when running something that requires root privileges like the synaptic package manager. What else are you being asked for passwords for?

---

### Post by risknothin on 2006-03-21
passwords: i used to not get asked that and i liked it.

hard drives..  Yeah i do and both say they are unreadable

---

### Post by manicka on 2006-03-21
[QUOTE=risknothin]passwords: i used to not get asked that and i liked it.

hard drives..  Yeah i do and both say they are unreadable[/QUOTE]

OK, run 

```
sudo gedit /etc/fstab
```

in a terminal

then change the you ntfs entries to

```
/dev/hda2 /media/hda2 ntfs defaults,umask=002,nls=utf8 0 0
/dev/hda5 /media/hda5 ntfs defaults,umask=002,nls=utf8 0 0
```

reboot

As for not being asked for passwords I can't help you there. You're asked for passwords for good reason. Withou them you are operating in an insecure environment. If you bypass this type of protection then you may as well run windows.

---

### Post by risknothin on 2006-03-21
worked perfect thank you!

---

### Post by manicka on 2006-03-21
np :D

---

### Post by linbetwin on 2006-03-21
manicka, I edited my fstab with **nls=utf8,umask=0222**, without **defaults**. What is the difference between your suggestion at post #9 and my configuration?

Also, why does Ubuntu mount Windows partitions (Dapper does it by default) if it only gives read access to root? Is this a bug, or is it intended that way? I know it's not safe to write to ntfs, but reading is safe.

---

### Post by manicka on 2006-03-21
[QUOTE=linbetwin]manicka, I edited my fstab with **nls=utf8,umask=0222**, without **defaults**. What is the difference between your suggestion at post #9 and my configuration?

Also, why does Ubuntu mount Windows partitions (Dapper does it by default) if it only gives read access to root? Is this a bug, or is it intended that way? I know it's not safe to write to ntfs, but reading is safe.[/QUOTE]

hmm, the finer points of fstab escape me. If it works, use it.

The windows drives are mounted as read only because writing to ntfs is not supported. I think it's a simple as that or do you mean mounted on the desktop? If so, I commented my ntfs drive out in fstab until that bug is fixed.

---

### Post by linbetwin on 2006-03-21
I know they are mounted read only and I understand the reason, but they are only readable by root.

---

### Post by AndrewCaul on 2006-03-21
[QUOTE=linbetwin]I know they are mounted read only and I understand the reason, but they are only readable by root.[/QUOTE]
I don't recall that happening with me. I've got my NTFS partition up and running, everything accessible, and I don't need root access to read it.

---

### Post by manicka on 2006-03-21
[QUOTE=linbetwin]I know they are mounted read only and I understand the reason, but they are only readable by root.[/QUOTE]

You should be able to access those drives as a normal user. What happens when you navigate there in nautilus?

---

### Post by linbetwin on 2006-03-22
Nautilus says it cannot display the contents. The Properties dialog shows that the mounted partitions belong to root. If I open Nautilus with gksudo and try to change owners or permissions, it says it cannot do this because the folder is on a read-only drive or sth. So I opened fstab, found **ntfs defaults 0 0** and I replaced **defaults** with **nls=utf8,umask=0222**, as instructed in the unofficial Ubuntu guide.

---

### Post by manicka on 2006-03-22
So, you have solved your problem then?

---

### Post by linbetwin on 2006-03-22
[quote=manicka]So, you have solved your problem then?[/quote]

Yes, I have solved it, but I didn't know whether this was a bug or the intended behaviour.

---

