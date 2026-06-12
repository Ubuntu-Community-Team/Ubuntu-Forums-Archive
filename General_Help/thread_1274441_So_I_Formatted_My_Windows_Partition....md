---
title: "So I Formatted My Windows Partition..."
date: 2009-09-24
forum: General Help
---

### Post by Morticutor UK on 2009-09-24
...while trying to format an SD card at the end of a long and frustrating day, I accidentally formatted sda1 (my windows/boot partition) rather than sdb1 (SD card).  

Yeah, I know.  

Now I've gotten Windows back into its previous partition, but I can't seem to find the file structure for my Ubuintu install.  Instead of the tree I get this:

[IMG]http://img.photobucket.com/albums/v713/morticutor/Screenie.jpg[/IMG]

I'm not quite sure what's going on here; I checked at the time and **only** the first partition had lost its data, but now I can't find my home folder.  

Does anyone know where I should be looking?

---

### Post by HermanAB on 2009-09-24
Windows doesn't play well in groups and overwrites the boot loader when you install it.  Some searching on the forum and with Google will find numerous threads on how to fix it.

---

### Post by Darkwing-Duck on 2009-09-24
Here is a guide for restoring grub. I hope this will help you.
 
[http://gwos.org/udsf/doku.php/core:grub:restore](http://gwos.org/udsf/doku.php/core:grub:restore)

---

### Post by Morticutor UK on 2009-09-25
So, the filesystem should still be there, albeit unseen?

Cool, thanks.  I have a couple of articles to knock out this morning, but I'll try this later and report back.

---

