---
title: "CD image"
date: 2009-10-21
forum: General Help
---

### Post by Sam5472 on 2009-10-21
Is there an equivalent of a mac disk image on Ubuntu, for both cdr and dmg?

---

### Post by Sam5472 on 2009-10-22
.

---

### Post by ColdFFF on 2009-10-22
Im not entirely sure what you are asking.

Disk images (.iso, .dmg, .nrg, .mds etc.) are image files, and can exist on any operating system you use.

Perhaps what you mean to ask is "Is there a disk image mounter capable of mounting proprietary mac disk image formats?" ?

---

### Post by Sam5472 on 2009-10-23
I don't want a program that will read a proprietary mac format. I want a program that would create a image similar in functionality to a dmg image, so that I can run a program that requires a cd without inserting said cd.

---

### Post by alphaniner on 2009-10-23
brasero (Applications -> Sound and Video) can make a cd image for you.  There's also k3b which I've heard is better.  You then mount said image to an empty directory.

This doesn't necessarily mean you will be able to use it to run a program though, particularly if the cd has copy protection.

---

### Post by Jayferd on 2009-10-23
I think for this what you want is an .iso.  If you go to Places->Computer, just right-click on the CD you want to rip, and there should be an option like "Make disc image".  Follow the prompts and you'll have yourself an iso file.

To mount it, right-click and open with "Archive Mounter".

Also, if your iso happens to be of a dvd movie, you can open it with gxine without even mounting it by typing 
```

gxine dvd://path/to/file.iso

```

AWESOMEZORZ.

---

### Post by alphaniner on 2009-10-23
> **Jayferd said:**
> If you go to Places->Computer, just right-click on the CD you want to rip, and there should be an option like "Make disc image".  Follow the prompts and you'll have yourself an iso file.

To mount it, right-click and open with "Archive Mounter".

Cool, I didn't know this.

---

### Post by vinutux on 2009-10-23
Mounting any images is not a problem under linux.........

---

### Post by Sam5472 on 2009-10-23
Thanks, everyone.  This seems to work just fine, proprietary formats are especially annoying (apple).

---

