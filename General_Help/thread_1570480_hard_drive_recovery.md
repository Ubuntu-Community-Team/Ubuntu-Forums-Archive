---
title: "hard drive recovery"
date: 2010-09-08
forum: General Help
---

### Post by aravenscroft on 2010-09-08
hey, I've been using ubuntu about a year, so I have a fair amount of experience with it. today I was trying to install ubuntu on my new laptop, which doesn't have an optical drive. I don't have a usb stick, so I attempted to partition my external hard drive. I stupidly clicked "erase disk" on startup disk creator and erased the entire drive instead of the partition.

I want to get back the files I had on this external. I searched and managed to find that people had been successful with testdisk. when I choose to analyse, it only finds the partition I created for the live cd. when I choose advanced, I can find my older partition (FAT32) but when I choose to undelete I get:

```
No file found, filesystem seems damaged.
```when I choose boot I get:

```
Boot sector
Bad

Backup boot sector
Bad

Sectors are identical.

A valid FAT Boot sector must be present in order to access
any data; even if the partition is not bootable.
```I searched but I couldn't find anyone receiving this error message or how to deal with it.

so I tried using photorec. photorec is recovering all of my documents currently but without the filenames and file structure, it's more or less worthless. does anyone have any other suggestions? thanks.

edit: apologies, I realise this should probably go in the hardware section.

---

### Post by aravenscroft on 2010-09-09
bump. any ideas?

---

### Post by Mark Phelps on 2010-09-09
> **aravenscroft said:**
> bump. any ideas?

I've found from bitter experience that MS Windows utilities do the best job of recovering files from FAT/FAT32/NTFS partitions.  But, you will need an MS Windows PC to run them.

IF you have that option, consider going to the Runtime Software site, downloading and installing GetDataBack for FAT, and running it against your external drive.  It won't actually recover anything, but it will tell you what it found.  To do the recovery, you have to purchase it.

But, it's your data, your money -- and your choice.

---

### Post by aravenscroft on 2010-09-09
hmm, makes sense. I do have windows 7 booted on one of my machines but there's nothing really worth paying for on the drive that couldn't be identified in photorec's backups.

thanks for your help.

---

