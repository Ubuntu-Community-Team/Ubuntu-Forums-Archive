---
title: "Shortcut to windows desktop?"
date: 2009-12-06
forum: General Help
---

### Post by linux_dream on 2009-12-06
I'm dual booting Ubuntu with windows XP.  
I'd like to know if I could easily reach my windows xp desktop, like if I could do a shortcut for a directory or so.
The only way I found until now is to open my windows disk and search for the desktop which isn't really easy.  So I'd like to create a shortcut so that if I click on it, it directs me over my windows desktop.

I'm sorry if it has already been asked (quite likely).

Thank you!

---

### Post by Matt__ on 2009-12-06
try ```
sudo apt-get install ntfs-config
```allow write support when promted

you will have your windows drive mounted on ubuntu desktop

Once you have ubuntu mounting your ntfs drive you can right click ubuntu desktop and 'create new launcher' to a location of your choice
(you may have to select a file when you use the browse option, but just edit the path back to documents (or wherever) and it will work fine)

---

### Post by sikander3786 on 2009-12-06
I think you should right click the folder you want to make the shortcut of and click "Create Link" or "Make Link" (I am not in front of Ubuntu PC so don't exactly remember the text). Then drag that link to your Ubuntu Desktop.

One more thing, your Windows drive is most like to be "NTFS" so you will have to set it to auto mount on start up otherwise on restart you'll not be able to access the directory through shortcut before mounting the drive.

---

### Post by linux_dream on 2009-12-06
Thank you both!
Before doing it, I should mention that I have only one disk partitioned (Windows uses 2 parts, FAT32, not NTFS).
Is it the same procedure?  What if I want to undo the changes?

---

### Post by Matt__ on 2009-12-06
If the partitions are fat32 they should automount anyway (?) not entirely sure.
In which case just go straight to 'create new launcher'.


//PS. why have you got xp on fat32?

---

### Post by linux_dream on 2009-12-06
> **Matt__ said:**
> If the partitions are fat32 they should automount anyway (?) not entirely sure.
In which case just go straight to 'create new launcher'.


//PS. why have you got xp on fat32?
Thanks!  I've done it.  
They sold me the computer with windows xp on a fat32 disk.  Should I convert into NTFS?

---

