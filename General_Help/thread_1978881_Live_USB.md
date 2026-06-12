---
title: "Live USB"
date: 2012-05-12
forum: General Help
---

### Post by evilsoup on 2012-05-12
I'm using a persistent live USB to try out 12.04. I'll get around to installing it properly soon, since it all seems to work well enough, but I have one question: if I install software onto the persistent USB, will that software be installed along with the OS when I do that? This will be a fresh install, not an upgrade.

---

### Post by sudodus on 2012-05-12
Private files as well as installed programs will be stored in the casper-rw file or partition, which is overlayed the original file system. So they are persistent (remain after reboot or poweroff). But it is not possible to update/upgrade the kernel.

I think the biggest disadvantage compared to an installed system is that it takes a lot of time at reboot or poweroff to write the live system to the USB drive, and if you are have not patience or time enough, the system will be corrupt, and you have to start with a clean casper-rw file or partition again. *Edit: A flashing LED indicator makes it easier to wait long enough ;-)*

If you want to run a persistent live or portable system, you can also 'install' it the normal way, but to a USB drive instead of to an internal HDD. Then you can update/upgrade it without limitation (except the size of the USB drive).

---

### Post by evilsoup on 2012-05-12
Ah, I think I have maybe not made myself clear enough.

I know that the software will be stored on the USB stick, and that whenever I boot from it that software will stay there (which is a really cool function btw). What I am asking is: when I get around to installing *from *the live USB stick *to* my laptop's harddrive, will that software still be there? Or will it only give me the default software? I am currently forced to use a 3g dongle, which has a data limit, so I kind of need to know...

(PS not sure about Unity overall, but the HUD is a pleasure to use, even if it is laggy - but I put that down to running of a live USB, I'm sure it will be snappier when it is properly installed).

---

### Post by sudodus on 2012-05-12
I tested these things during the beta testing of 12.04 of Lubuntu:

The language, timezone, user name and computer name are stored from one installation to another, when done with a persistent live system.

But added software and personal files (documents, pictures etc) are ***not*** installed. Only the original system (without the content of the casper-rw file) will be installed (with the above exceptions) if I remember correctly.

*Edit: I had installed htop in the persistent system, but it was not transferred during the install procedure to the system on the HDD.*

---

### Post by evilsoup on 2012-05-12
:(
Oh well. Thanks for the answer.

---

