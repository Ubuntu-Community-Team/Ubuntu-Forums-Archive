---
title: "The Blue Screen"
date: 2010-10-15
forum: General Help
---

### Post by jr_herman on 2010-10-15
Hello All,

Have a problem...

When I boot my PC up I get the blue screen that does not let you pass go or collect $200. These are the following messages I'm getting. (Pics included)

1.GDM could not write new authorization entry to disk.
2.Could not start the X server

Any ideas?

---

### Post by jespdj on 2010-10-15
Well, the first screen contains a clear hint: there is not enough disk space. Is your Ubuntu partition full?

---

### Post by jr_herman on 2010-10-15
I'm going to assume it is. Lets assume yes. how do i get in to delete stuff to clear space?

---

### Post by sendblink23 on 2010-10-15
> **jr_herman said:**
> I'm going to assume it is. Lets assume yes. how do i get in to delete stuff to clear space?

Boot a LiveCD, you can access your files through there... and pass wte you want to an external hard drive or usb flash drive... and then erase them from your internal ubuntu install

---

### Post by jr_herman on 2010-10-20
Accessing the files through a live CD worked. Had to do everything from the terminal using "sudo" before commands because from the live cd you do not have proper permissions to just delete.

---

### Post by jr_herman on 2010-10-20
Thanks

---

