---
title: "user doesnt have write permissions to floppy"
date: 2010-01-07
forum: General Help
---

### Post by nerdy_kid on 2010-01-07
Hi all, so i have a limited user (my dad) on Jaunty who has no write access to his floppy disks.  Nautilus gives a permission denied error, and i discovered that root owns the floppy drive, thus allowing his read-only.  (that write tab on the floppy in on btw).  However, when i login as a admin, nautilus says that user has write access.  ??? I check the user's user privliges and everything exept "administer the system" is checked.  I can copy files on it by logging in as root.



Thanks in advance!

---

### Post by hobit on 2010-01-07
Its been a long time since I've used a floppy but couldn't you add a line to /etc/fstab similar to a cdrom with the user flag, thus allowing normal users to mount?

Just a thought.

---

### Post by nikhilbhardwaj on 2010-01-07
aren't floppies extinct 
havent used one for years

---

### Post by nerdy_kid on 2010-01-07
> **nikhilbhardwaj said:**
> aren't floppies extinct 
havent used one for years

LOL yeah basicly but my dad uses a 350Mhz win98 for writing papers and floppy is the easiest way to go to transfer them.

what mixes me up is that from my account (sudoer) it says that my dad mounted the floppy, but from my dad's account (non-sudoer), it says root did.  ?

---

### Post by warfacegod on 2010-01-07
> **nikhilbhardwaj said:**
> aren't floppies extinct 
havent used one for years

I haven't even *seen* one in years. I think I've got some buried at the bottom of box of old desktop parts that I labeled in my brain: "Ignore this for the next 2 decades".

---

