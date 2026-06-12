---
title: "(live)DVD burning issues"
date: 2009-12-26
forum: General Help
---

### Post by User0123 on 2009-12-26
I'm having trouble when burning an ISO to a DVD-RW using brasero.

I insert the blank disc, choose the ISO, and let it burn.
I receive no errors, the burning completes successfully, but upon rebooting my PC the disc is ignored as if the tray was empty.

Yes I have BIOS configured correctly, other live CDs and DVDs boot fine for me, I have tried them, those are DVDs that I have gotten from magazines etc, not ones which I have created myself.

And yes, I have checked the md5sum of the iso and compared it with the one listed on the site.

I just have no idea what could be causing this problem, I don't even have any errors to start with.

EDIT: I have just noticed that even after it saying the burn has completed successfully the disc remains blank? Am I making some fundamental error here? do I need to run brasero with root privileges or something?

---

### Post by User0123 on 2009-12-26
Using 64bit Ubuntu here by the way, but I'd guess this is a brasero issue?

Also my hardware works fine when burning software using windows, but I haven't even bothered to boot into wind0ze for months, I don't really wanna have to start that just to burn a disc :P

---

### Post by MooPi on 2009-12-26
Have you checked to see if drive is reading at all ? Inset a media disc to check.

---

### Post by User0123 on 2009-12-26
Yes, I have double checked just now, inserting a disc with some other software on, and that can be read fine, the drive is working, as I said in my original post, I have attempted to boot other Live CDs/DVDs and they are working.

It just that I cannot create my own.

---

### Post by MooPi on 2009-12-26
Try this ```
dpkg --get-selections> installed_software
``` in terminal. This will drop a text file of all apps installed. Check for dvd+rw-tools.

---

### Post by User0123 on 2009-12-26
dvd+rw-tools                    install


Yup it's there.

---

### Post by hariks0 on 2009-12-26
Try invoking Brasero from the menu instead of using the autoplay option.

---

### Post by User0123 on 2009-12-26
> **hariks0 said:**
> Try invoking Brasero from the menu instead of using the autoplay option.


Tried that already, no difference

---

### Post by MooPi on 2009-12-26
Drawing a blank at the moment but have opened Brasero myself and looking for possible solution. My only suggestion is to remove Brasero and reinstall to check if your missing a dependency.

---

### Post by User0123 on 2009-12-26
> **MooPi said:**
> Drawing a blank at the moment but have opened Brasero myself and looking for possible solution. My only suggestion is to remove Brasero and reinstall to check if your missing a dependency.

I'll give that a shot, this is really puzzling me at the moment too. If this doesn't work I'm going to slap the ISO on my flash drive and have a shot at burning it on my dads XP machine.

---

### Post by taurus on 2009-12-26
You can always try k3b as another option.

---

