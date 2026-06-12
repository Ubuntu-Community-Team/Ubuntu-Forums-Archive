---
title: "Whats the best to configure auto mount for NTFS drives?"
date: 2011-05-16
forum: General Help
---

### Post by agrayray on 2011-05-16
I have a dual boot setup with a fair amount of files in my windows volume.

I noticed that the Ubuntu 10.4 GNOME version (at least) does not auto mount my NTFS drive.

Of course as I have seen from various post this gets annoying when opening up a program that loads previous files before I for ex, click the '110GB FileSystem' icon from Nautilus or similar...that seems to mount it for me then...

I want my 110GB NTFS volume to mount automatically so I dont have to do this process everytime I reboot.

I found a post on the forum (the latest one I could find) below that recommends installing ntfs-config.

Can some please re if this is still the way to do it?

The post is from May 2008 but mentions 10.10 (via edits) so I'm confused and wondering if there is an easier/default way..or this is still the way to go?

After several screw ups editing system files manually, Im very cautious about doing it in this case because its a work computer and frankly the uninsttall or editing the fstab manually worries :( me.

Thanks in advance!

[http://ubuntuforums.org/showthread.php?t=785263](http://ubuntuforums.org/showthread.php?t=785263)

---

### Post by gsmanners on 2011-05-16
You probably want to try something a bit more up to date:

[http://ubuntuforums.org/showthread.php?t=1668813](http://ubuntuforums.org/showthread.php?t=1668813)

---

### Post by pablopancho on 2011-05-16
Personally I use a little program: **pysdm** (Storage Device Manager). You can find it in default Ubuntu repos so check it out in software center or synaptic. I configure each of the disks with default settings and it works flawlessly.

---

