---
title: "dd command killed my operating system...HELP"
date: 2009-11-07
forum: General Help
---

### Post by sizemore101 on 2009-11-07
Okay. So I had a corrupted external hd and from what I saw the best way of retreiving information was by creating an image of it via ubuntu. So I put the following into terminal...

[INDENT]sudo dd if=/dev/sdb of=/dev/sda[/INDENT]

I presuming this is not what I should have done as it wiped out my hd. Oh well. At which point I reinstalled Ubuntu 9.10... it worked briefly... but in the process of trying to get the internet to work, it crashed. 

Now when I try and boot up it lets me login but instead of bringing up the desktop, a white terminal box comes on the upper left corner of the screen. I cannot reinstall Ubuntu -- either 9.04 or 9.10 -- as it doesn't recognize the cds. 

Any help on what to do? Thanks.

---

### Post by sizemore101 on 2009-11-07
Bumpity Bump.

---

### Post by Chronon on 2009-11-07
It seems that you destroyed the partition table and overwrote a bunch of stuff on /dev/sda.

You should be able to boot a LiveCD even with no HD attached.  What do you mean when you say that the CDs aren't recognized?

---

### Post by sizemore101 on 2009-11-07
But if I destroyed my partition table, why is the reinstalled operating system not working? And when I say I can't install a live cd. I mean after I select CD/DVD/CD-RW Drive on the boot menu... it pretends I didn't do that and just boots normally. Is this just a complete hardware issue?

---

### Post by Chronon on 2009-11-07
If your drive is SATA then it should be hot pluggable.  Maybe you can force the system to boot the LiveCD by temporarily disconnecting the HD.

---

### Post by Chronon on 2009-11-07
I don't know why the previous attempt to reinstall didn't work.  I can only suggest that you try to get the LiveCD running and then try again with a known good LiveCD.

---

### Post by sizemore101 on 2009-11-07
New detail that I noticed.

On the login screen, at the bottom there is the language option and the keyboard option... I forget, but it seems like there was another option previously. Does this mean something? Thanks.

---

### Post by sizemore101 on 2009-11-07
Additional information: On the boot it says there is an error mounting the filesystems. I can't get exactly what it says. Is there a way to launch the cds from the terminal or the console? There is nothing wrong with the cds.

---

### Post by diesch on 2009-11-07
What do you get if you run
```
 gnome-session
```
in the terminal box?

---

