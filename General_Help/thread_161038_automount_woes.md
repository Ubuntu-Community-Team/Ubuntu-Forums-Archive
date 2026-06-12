---
title: "automount woes"
date: 2006-04-16
forum: General Help
---

### Post by vavoem on 2006-04-16
When i stick in my usb pendrive konqueror opens a window pointing to media://sda1
but the pendrive is automounted in /media/usbdrive

how can i configure automount to mount the usb stick
in /media/sda1

or how can i configure konqueror to point to media://usbdrive?

---

### Post by aysiu on 2006-04-16
```
sudo umount /dev/sda1
sudo mkdir /media/sda1
sudo cp /etc/fstab /etc/fstab_backup
sudo kwrite /etc/fstab
``` Add in this line ```
/dev/sda1 /media/sda1 vfat iocharset=utf8,umask=000 0 0
``` Save ```
sudo mount -a
``` This assumes your USB pendrive (like most) is FAT16 or FAT32.

---

### Post by vavoem on 2006-04-17
Thank you it points to the right point now except when i clicked it i get a message only root can mount it.

I've changed umask000 to user and now it works! thanks

---

### Post by Titus A Duxass on 2006-04-17
It sounds like you need to change the permissions to let users do it.

I use sudo chmod 777 /the/filename, so try:

sudo chmod 777 /media/sda1

---

### Post by xenmax on 2006-04-17
[QUOTE=Titus A Duxass] I use sudo chmod 777 /the/filename, so try:

sudo chmod 777 /media/sda1[/QUOTE]

if filesystem on usb is fat, i dont think chmod will work (at least thats my understanding) 
Anyway, if he says umask=000 worked, thats probably what it was.

---

### Post by vavoem on 2006-04-17
no no you misunderstood

i took away the umask000 bit and replaced it with user and that makes it work
so my line in fstab is now

/dev/sda1 	/media/sda1 	vfat	 iocharset=utf8,user 0	 0

---

