---
title: "viewing contents of other drives"
date: 2006-04-13
forum: General Help
---

### Post by Gaia on 2006-04-13
Hi,

I'm new to ubuntu/linux and just finished installing, everything went fine and is working well, i'm just wondering how i can browse the contents of my partitions/harddrives that ubuntu aren't apart of?

It says that i don't have the permission to view the contents of it. I have Windows XP Pro installed on one hard drive and ubuntu and another partition on a second hard drive. I want to be able to access the Windows and other partition files.

How can i set that up? Or is that something I have to do through Windows?

Thanks!

---

### Post by dave9191 on 2006-04-13
[http://ubuntuguide.org/#mountunmountntfs](http://ubuntuguide.org/#mountunmountntfs)

And just a note, you can't write to NTFS partions, just read. 

--
Dave

---

### Post by Gaia on 2006-04-13
Thanks Dave!

---

### Post by Gaia on 2006-04-13
hey, seems to be a problem.  I'm trying to use umount /media/windows/ and it says that it's not found so i tried to unmount it on the Ubuntu desktop and it says that I can't because i dont have adminstrative permissions?

---

### Post by nastavirss on 2006-04-13
I dont think there is a folder windows in /media...i think its hda<no>...go to /media and check it out.

---

### Post by justleen on 2006-04-13
[QUOTE=Gaia]hey, seems to be a problem.  I'm trying to use umount /media/windows/ and it says that it's not found so i tried to unmount it on the Ubuntu desktop and it says that I can't because i dont have adminstrative permissions?[/QUOTE]


use sudo umount

---

### Post by Gaia on 2006-04-13
ah, thanks, it's working now!

---

