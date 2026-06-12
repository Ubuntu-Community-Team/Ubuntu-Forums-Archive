---
title: "Very long copy operation on sd card"
date: 2009-08-05
forum: General Help
---

### Post by t0p on 2009-08-05
I have an EeePC 701 - the model with a 4GB SSD.  I run eeebuntu on it.  Because the internal disk is so small, I also have a 4GB SD card permanently in the card reader, and I have /home mounted on that SD card.

I have noticed that if I copy a large file from one location on the SD card to another location on that same card, it takes an awfully long time.  For example, I copied a 200MB file from my home directory to my desktop subdirectory, and the *cp* operation took over 30 seconds!  But if I *move* the file from the home directory to the desktop subdirectory (ie, using the *mv* command), the operation was completed "instantly".

I've never noticed this behaviour before.  Is this to be considered "normal"?  Or is something wrong with the card... or, heaven forfend, with the computer?

---

### Post by P4man on 2009-08-06
seems normal to me. 200Mb in 30s is 6-7Mb/sec. Thats about what you'd expect from a (cheap) ssd card. That its instantaneous on your internal drive, is probably because ubuntu doesn't write it yet, but caches the write and writes later in the background. It won't do so with a removable device, because you could eject the drive before it has completed the write, corrupting the drive.

I think you can change that behavior, but Im not sure how, and its probably not a good idea either, unless you rarely or never remove the card and know how to eject it safely.

edit: I reread now, and you moved the folder on your internal ssd. Well, its normal that that is instantaneous: it doesnt do anything other than changing a small reference to the file, it doesnt have to write 200Mb. Try copying it, and it will take a lot longer.

---

### Post by burmanabhay88 on 2009-08-06
> **t0p said:**
>  the *cp* operation took over 30 seconds!  But if I *move* the file from the home directory to the desktop subdirectory (ie, using the *mv* command), the operation was completed "instantly".


This is normal. the copy command creates an additional copy of the file, and for a file of that size, that's the amount of time it'll take. The move command however, doesn't relocate the file as such, just it's entry in the inode table (a place where the entry of all files is kept).

---

### Post by sponsoredwalk on 2009-08-06
Moving from your home folder to the desktop is like telling your computer the file should now load from the desktop instead, it's still the same file and it never takes time to do this. Copying a file from my home folder to the desktop however would take time but it should be really quick, far quicker than copying to a disk connected via usb as you are using the internal hardware of your pc to do the job.
Also, 30 seconds is pretty sweet for you to copy 200mb to an external sd card, i had 2 phones, the older one would take literally 6 hours to copy 2 gigs of music onto it, i had to pre-plan everything and create a ready-made folder on my pc of all the music i wanted, copied into this folder (which was quick as it was on my pc - like the home folder to desktop issue above) to do a straight copy-paste job. The newer one would take about an hour, maybe less, so i could copy 1 file and then look for another random one and copy that nearly straight away coz my browsing time would usually equal the time it took to copy the file onto my phone.

---

