---
title: "Adding a second Hard Drive"
date: 2006-01-25
forum: General Help
---

### Post by chaser001 on 2006-01-25
I'm realy new to linux & Ubuntu...I'm trying to add a 250gb hd to my Breezy box...I've got it formated as ext3 but I can't figure  out how to creat a mount point so that I can access it....My whole point for this box/HD is to use the 250 drive as storage across my network.  I've got samba running & working using the HDA but I want to add this second HD for more storage.

Thanks

---

### Post by Gcool on 2006-01-25
If your disk is detected and formatted and so on, you just need to create a mount point, and mount the disk there.

Example (assuming the disk is hdb and has 1 large partition):

mkdir /mnt/disk2
mount /dev/hdb1 /mnt/disk2

---

### Post by chaser001 on 2006-01-26
I made the directory w/out any problems however when I try the mount command I get "mount: Only root can do that"

So how do I login as root on Ubuntu?

EDITED---------

nevermind...I added sudo infront of the command and it all worked out....Thanks!!

---

### Post by StefanoCole on 2006-01-27
You do not need to log as root. Use the "sudo" command:

sudo mount /dev/hdb1 /mnt/disk2

Stefano

---

### Post by ZAKhan on 2006-01-27
When I do **mkdir /mnt/disk2** it gives me an error :

[COLOR="Red"]mkdir: cannot create directory `/mnt/disk2': Permission denied[/COLOR]

I have tried to create it with sudo and works but then users donot have access to this directory!

---

### Post by kscelt on 2006-01-27
Go into the permissions on the drive as root and enable permissions on the drive for read write

---

### Post by Ocxic on 2006-01-27
use sudo before any command that give you that error, sudo is a special way of granting root access for a short period of time so you can run a program/command with root access, wich is much safer then login in as root. ie:
```
 sudo mkdir /media/disk2  (making the mount point in media will put an icon on your desktop, and add it to the "computer" locaton int your places menu)
then 
sudo mount /dev/hdb1 /media/disk2
``` and your done.

---

