---
title: "using programs from different installations?"
date: 2010-09-27
forum: General Help
---

### Post by garyed on 2010-09-27
I have three different versions of Ubuntu on my computer on three separate partitions, they are Feisty, Hardy & Lucid. Every time I install a new OS I install the same programs all over again. Is there a way to use a program that is already installed on Hardy while I'm running Lucid?

---

### Post by andrewthomas on 2010-09-27
Not a good idea.

---

### Post by WorMzy on 2010-09-27
Kind of, with chroot.

[https://help.ubuntu.com/community/BasicChroot](https://help.ubuntu.com/community/BasicChroot)

EDIT: Ignore the "Creating a chroot" section, no idea why that's even there. Just mount your other Ubuntu installation to /mnt (or wherever), and then start from "Setting-up the chroot".

Also, you may want to "mount -o bind" /dev and /sys, as well as /proc.

---

### Post by Mark Phelps on 2010-09-27
> **garyed said:**
> ...Every time I install a new OS I install the same programs all over again...

If you're talking about apps you download and install yourself, by building them from the same source code each time, then what you say is true.

But, if they are apps you install from Synaptic or from the Software Center, these are typically updated with each major Ubuntu release.  So, they're not really the "same programs" each time.  They're newer versions of the programs -- each time.

So, you would need to confirm that the program version is the same for each distro version -- before you trying reusing it across distros.

---

### Post by garyed on 2010-09-27
Most of them are in synaptic but not all so I guess it wouldn't be practical but I would like to know how to do it for a program that has not been updated. I read a little about chroot & don't really understand it too well. It does seem that chroot would be the best way to go if I wanted to try it.

---

### Post by garyed on 2010-09-29
> **Mark Phelps said:**
> If you're talking about apps you download and install yourself, by building them from the same source code each time, then what you say is true.

But, if they are apps you install from Synaptic or from the Software Center, these are typically updated with each major Ubuntu release.  So, they're not really the "same programs" each time.  They're newer versions of the programs -- each time.

So, you would need to confirm that the program version is the same for each distro version -- before you trying reusing it across distros.

Lets assume the version hasn't changed on a program I installed through apt-get or synaptic. How would i use it accross distros. Just using the path to the executable wouldn't work would it?

---

