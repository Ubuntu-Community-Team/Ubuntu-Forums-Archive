---
title: "Installing to SD card eeebuntu"
date: 2010-02-06
forum: General Help
---

### Post by dchurch24 on 2010-02-06
Hi all,

I got my daughter an eeepc for xmas, but it only has a 2gb 'hard drive'. With the OS and aMSN etc... that is pretty much all used up.

I also got a 2gb SD card for it.

Is there a way I can get Synaptic to install software on the SD card rather than to the internal drive?

---

### Post by efflandt on 2010-02-06
To boot from SD, it would usually need to be in a USB SD card reader, unless a memory slot on the computer is internally connected by USB.  For example my Toshiba laptop will not boot from its memory slot (different type of block device), but will boot same SD or microSD in a USB card reader (or SD slot on my desktop internally USB connected).

System > Administration > USB Startup Disk Creator can boot install/live iso with persistent data.  With that you could add packages, but should avoid updates because you cannot change the boot kernel and some other things that run before persistent data is mounted unless you modify the iso first, or some compressed data on the flash memory.

2 GB is probably not enough room for a regular full install unless there is an Ubuntu version for eeepc that is smaller than the 2.7 GB or so used for regular Ubuntu.  So 4 GB is usually the absolute minimum for full install, but 8 GB is generally considered the minimum practical.  And for full install you would need to remember to use the last **Advanced** button in installation summary to put grub2 in the mbr of the USB drive instead of main drive.

---

### Post by mdurham on 2010-02-06
He didn't ask about booting from it.
What you could do is to format the SD card and copy your /usr directory to it. Then replace the original /usr with a link to the usr on the SD card. That would free up a lot of space and all new installs would go to the SD card.

---

### Post by frt975 on 2010-02-06
Did you mean /usr ?

---

### Post by mdurham on 2010-02-06
> **frt975 said:**
> Did you mean /usr ?
Sorry, yes I meant /usr, it's late!

---

### Post by dchurch24 on 2010-02-06
Excellent - thanks for the replies.

I presume I could do the same with the /home folder(s) too?

Would I just create a sym link (sn -l) as root in the existing /usr folder?

---

### Post by mdurham on 2010-02-06
> **dchurch24 said:**
> Excellent - thanks for the replies.

I presume I could do the same with the /home folder(s) too?

Would I just create a sym link (sn -l) as root in the existing /usr folder?

Assuming you copied /home and /usr to the SD card, you would create two links from / one named home and the other usr.
BUT, I don't see how you can do this from the working system because there will be a period of time when /usr and /home will not exist (in the working system). It might be possible, but someone more knowledgeable than me might be able to advise you. I would do it by booting from a memory stick but I guess you don't have one of those. You could install Puppy Linux on the SD card and boot from that, it would only take up a small amount of space.

---

