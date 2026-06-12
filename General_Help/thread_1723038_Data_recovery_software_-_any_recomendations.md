---
title: "Data recovery software - any recomendations?"
date: 2011-04-06
forum: General Help
---

### Post by bobnutfield on 2011-04-06
Hello Everyone,

My boss recently went on an important charity event, and took numerous 
photos for personal and media use.  Somehow, the SD card in the camera became corrupted and the SD disk will not even mount.  It does show up in
lsusb using my netbooK:

```
Bus 001 Device 002: ID 0c45:62c0 Microdia Sonix USB 2.0 Camera

```

But it does not show up anywhere else to mount it.  The data is corrupted, but to what degree I do not know.  The disk is a standard camera SD card, so I assume it is a FAT file system.

I have heard of some forensic software that can recover data on broken disks, but I have never attempted this.  Can anyone suggest a way to attempt this?

Any help will be greatly appreciated as this was a VERY important event for our company.

---

### Post by wolfen69 on 2011-04-06
Plugging the SD card into a card reader would then show it to be disc volume on the computer, making it easier to read. I have used Magic Rescue with success. It is command line only, but works well.

---

### Post by bobnutfield on 2011-04-06
> **wolfen69 said:**
> Plugging the SD card into a card reader would then show it to be disc volume on the computer, making it easier to read. I have used Magic Rescue with success. It is command line only, but works well.

Thank you for your reply.  Plugging in the card does not mount it.  It will only show up in the lsusb listing.  If it would mount, I could see the extent of the data corruption.  Is there any software for accessing a disk that will not mount?

---

### Post by tredegar on 2011-04-06
Can the camera read the card and see the photos? If so, there's hope.

Try **photorec** (it's part of the **testdisk** package).

It's also worth trying another card-reader (some of them are *useless*)

---

### Post by bobnutfield on 2011-04-06
Thanks, but I think this is a futile effort.  If I can't get to the disk in some manner, I cannot run any software to even try.  It will not mount and does not appear to even be recognized when it is plugged in.  Photorec looked promising but not if it can't be found.

Thanks again

---

### Post by conradin on 2011-04-06
plug the camera into the usb what eva on your puter, and boot it. 
Then have a look at the dmesg file. and look for errors during boot.
```

sudo fdisk -l

```
show us that.

at the very least, you'll probably need to rebuild the file-system. Don't give up just yet.

---

### Post by bobnutfield on 2011-04-06
> **conradin said:**
> plug the camera into the usb what eva on your puter, and boot it. 
Then have a look at the dmesg file. and look for errors during boot.
```

sudo fdisk -l

```
show us that.

at the very least, you'll probably need to rebuild the file-system. Don't give up just yet.

Thank you your reply....

I had already tried those things.  fdisk -l does not show the disk, dmesg does not even mention its existence.  I have tried it in the built in SD card reader and in a USB card reader.  None of this even recognizes it as being plugged in.  That suggests that the card is so damaged it cannot even be hotpluged.

I don't know any other way to get to the disk.  All my windows computers give the same results.

Looks like its a goner.

Thanks again

---

