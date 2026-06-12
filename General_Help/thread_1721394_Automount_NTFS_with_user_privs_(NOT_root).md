---
title: "Automount NTFS with user privs (NOT root)"
date: 2011-04-04
forum: General Help
---

### Post by hoink on 2011-04-04
If I use Gnome to mount my NTFS drive, it mounts in /media/{UUID} with my user privileges.

But if I follow all the HOWTOs out there (using /etc/fstab), my NTFS drive is automounted, but with root privileges... (which is intolerable in this particular case).

How do I automount my NTFS partition with my user privs?

---

### Post by TeoBigusGeekus on 2011-04-04
Use the fstab method and then give
```
sudo chmod 777 /media/mountpointofyourdevice
```

---

### Post by hoink on 2011-04-04
Giving EVERYONE FULL ACCESS (your reply) is completely different than assigning to the drive my own user privileges.

I'll repost a new thread with a more specific question.

---

### Post by TeoBigusGeekus on 2011-04-04
[COLOR="Red"]((((((((You can then change the owner of the drive))))))
[/COLOR]
Then you can change the owner of the drive
```
sudo chown -R yourusername /media/mountpoint
```

---

### Post by hoink on 2011-04-04
Thank you for trying to help, but your suggestion is backward and unbelievably slow.  It's the incorrect approach for a login automount.  You're essentially mounting it in the wrong user context, then recursively fixing all the wrongly-mounted files.

---

### Post by TeoBigusGeekus on 2011-04-04
> **hoink said:**
> Thank you for trying to help, but your suggestion is backward and unbelievably slow.  It's the incorrect approach for a login automount.  You're essentially mounting it in the wrong user context, then recursively fixing all the wrongly-mounted files.

Sorry, what I meant was if you don't want to do the chmod-ing then do the chown-ing; not do post#2 first and then post#4.

---

### Post by hoink on 2011-04-04
I don't think you understand that neither chmod and chown/chgrp address the problem I'm asking... which is how to *MOUNT* the drive correctly.

---

### Post by TeoBigusGeekus on 2011-04-04
Ok, good luck.

---

### Post by ajgreeny on 2011-04-04
> **hoink said:**
> I don't think you understand that neither chmod and chown/chgrp address the problem I'm asking... which is how to *MOUNT* the drive correctly.
Install ntfs-config and use that to mount the partition with the user privileges you want.

You seem to believe that you can give the files on an ntfs partition the same sort of linux permissions as those on an ext# partition, but that is impossible.

You have to give the permissions and ownership to the mountpoint folder; that is what TeoBigusGeekus was trying to explain, I think.

If you want to use the fstab way, add a line with this format at the bottom of the file.
```
UUID=*66E53AEC54455DB2 /media/storage/*    ntfs-3g        auto,user,rw 0 0
``` but edit the UUID and mount point to suit your system.

---

### Post by TeoBigusGeekus on 2011-04-04
> **ajgreeny said:**
> Install ntfs-config and use that to mount the partition with the user privileges you want.

You seem to believe that you can give the files on an ntfs partition the same sort of linux permissions as those on an ext# partition, but that is impossible.

You have to give the permissions and ownership to the mountpoint folder; that is what TeoBigusGeekus was trying to explain, I think.

Yep.

---

### Post by hoink on 2011-04-04
Thank you both for your comments.

ajgreeny's comment forced me to re-examine the permissions I was getting from the Gnome-mounted drive compared to the fstab-mounted drive.  They were (except for a trivial difference with the directories) identical.  Only the owner/group was different between gnome-mounted and fstab-mounted mounts.

in this particular case, i guess it won't really matter if root owns all the files (fstab-mounted on startup) or if *I* own all the files (gnome-mounted manually)... because the permissions are essentially identical.

i was hoping to learn how to do via commandline what gnome does when you mount the drive with the GUI (ie, user-mounted, not root), but that'll remain a mystery for now.  but that's not really important anymore.  

thank you for your time.

---

### Post by QLee on 2011-04-04
[QUOTE=hoink]...
i was hoping to learn how to do via commandline what gnome does when you mount the drive with the GUI (ie, user-mounted, not root), but that'll remain a mystery for now.  but that's not really important anymore.  [/QUOTE]

In that case you'll probably want to study the manual page for the command, mount. Likely something along the lines of , mount -o, because that will allow you to use strings of options like you do in fstab.

---

