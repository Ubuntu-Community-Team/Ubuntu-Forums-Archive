---
title: "Permissions"
date: 2010-01-09
forum: General Help
---

### Post by tweee on 2010-01-09
Hey, posted from a thread at "apple users" since I really really, REALLY, need some help by (hopefully) tomorrow:

Hi,
so I installed ubuntu on my macbook pro, and now I get the infamous "still waiting for root device" when booting mac os x.
I was hoping there would be an easy way to fix this, but I couldn't find any solutions that worked (macbook pros don't have a BIOS, or any drives that are easily removable).

Anyway, so I have ubuntu working, and I need some files from OS X before I would consider reinstalling, etc. So I mounted the drive, went to users, etc. and it says that "I don't have the permissions necessary to view the contents of ****".
I did chmod 777 /media/os x/Users/* but that led to "Could not access: No such file or directory" (there's a space between os and x, i think it counts it as two commands or something and I can't rename the drive, oh the irony)

So if someone can give me a way to give myself the permissions to access my files, or maybe just to copy over the whole hard drive to my main computer, or maybe somehow solve the "still waiting for root device", I would be very grateful.
Thanks in advance.

---

### Post by Leppie on 2010-01-09
try using sudo with the mount command:
```
sudo mount -t ntfs /dev/sda1 /mnt/sda1
```

---

### Post by warfacegod on 2010-01-09
```
gksudo nautilus
``` will give you root permission in file browser, perhaps you could use that to get your files.

Alternatively:
```
sudo chown -R username:usergruop /media/drive name
``` will make you the owner of the drive but I don't know what that will do to your OSx install and if you only have one drive you'll be the owner of the ubuntu filesystem which I do know isn't a good idea.

---

### Post by warfacegod on 2010-01-09
> **Leppie said:**
> try using sudo with the mount command:
```
sudo mount -t ntfs /dev/sda1 /mnt/sda1
```

Macs use NTFS? Since when?

---

### Post by tweee on 2010-01-09
hey, so I did
gksudo nautilus, set file permissions, but it gives me
"The permissions could not be changed.

Sorry, could not change the permissions of 'os x': error setting permissions: Read-only file system"

the file system on that drive is "hfs+"

---

### Post by warfacegod on 2010-01-09
I meant to use root nautilus browse to the files you need and then copy them to somewhere in your linux install. Try Leppie's code with hfs+ replacing ntfs.

---

### Post by tweee on 2010-01-09
hey, thanks so much, it worked!

---

### Post by warfacegod on 2010-01-09
Exactly what worked? Mark as solved so other users can use your solution.

---

