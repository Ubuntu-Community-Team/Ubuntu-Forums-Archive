---
title: "Mounting a CD manually."
date: 2010-09-10
forum: General Help
---

### Post by Vigh on 2010-09-10
Hi I am trying to install some software through wine, but unfortunately the cd is not auto-mounting, is there a way I can manually mount the cd and continue installation?

---

### Post by ubulal on 2010-09-10
sudo mount /dev/sr0 /where/ever

If you didn't mess with the auto-mount configuration it is a sign of somewhat serious trouble when it's not auto-mounted...

---

### Post by Vigh on 2010-09-10
could the auto-mount failing be due to the fact that its a dvd?

---

### Post by ubulal on 2010-09-10
If the drive is CD-only, yes.  Unlikely otherwise.  Does manually mounting work?  If not, what do these commands print when executed in this order?:

sudo mount /dev/sr0 /mnt
dmesg | tail

---

### Post by Vigh on 2010-09-10
Problem solved! Just had to install medibuntu DVD support.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

Restarted and the DVD mounts perfectly now. Must be something to do with the file format of the DVD.

---

### Post by ubulal on 2010-09-10
???

What is on that DVD?  Software/Games or Video?  And what Medibuntu packages did you install exactly?

And what does "mounting" mean to you?  The file manager pops up and shows the files and folders on the DVD, right?

I'm just curios.

---

### Post by Vigh on 2010-09-10
Its not working still! LOL! Its weird, the file manager does not display the dvd at all, its definately a kernel problem as my hardware is running perfectly. Its a 12DVD set installation package of high-quality audio samples of instruments, but unfortunately after the 1st disc finishes and you go to install the 2nd disc, it just doesn't detect it, think i have to disable SCSI emulation on the cdrom drive. The DVD is not damaged and if I put the dvd in without running the installer for the instruments it detects the dvd perfectly.

---

### Post by Vigh on 2010-09-10
Intersting K3B detects it.

---

### Post by ubulal on 2010-09-10
Mmh I don't think you want to run audio production software on wine, do you?  I'd guess you're problem would be better discussed at a wine-specific list...

---

### Post by Vigh on 2010-09-10
It worked perfectly in previous version of wine and ubuntu. Its okay i've figured out a way to install it through wine successfully.

---

