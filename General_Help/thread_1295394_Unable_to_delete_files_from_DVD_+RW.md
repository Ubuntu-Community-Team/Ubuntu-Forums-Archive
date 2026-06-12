---
title: "Unable to delete files from DVD +RW"
date: 2009-10-19
forum: General Help
---

### Post by swappo1 on 2009-10-19
Hello,

When I try and delete a file from a DVD +RW I get an error: "media/cdr... file" cannot be deleted because it is on read only disk. I can't save files to the disk either. How do I change this to read write access so I can delete files and save new files to the disk?  Thanks

---

### Post by ubudog on 2009-10-19
Hi, this may or may not work.  But open a terminal :Applications>Accessories>Terminal and type the following: ```
sudo nautilus
```  After that your file manager (nautilus by default) will pop up and then just select the cd from the side.  Hope that helps.:)

---

### Post by swappo1 on 2009-10-19
I opened nautilus as root and tried to delete files on the disk and got an error message stating the disk is read only.

---

### Post by ubudog on 2009-10-19
Sorry.... Let me think about that..... will reply later. :)

---

### Post by -Zeus- on 2009-10-19
Do you know that your disk drive supports DVD+RW?  It could support only DVD+R.

---

### Post by mcduck on 2009-10-19
Unless the disk is formatted with a filesystem that supports packet writing (UDF, for example)  you won't be able to edit/remove individual files from it no matter if it's RW or not. Normal CD/DVD filesystem (ISO 9960) is always read-only, meaning that you can only erase and write the whole disk at a time.

Most likely you will also need to do some extra configuring to get packet writing to work directly from file manager, I don't think Nautilus supports that by default.

---

### Post by -Zeus- on 2009-10-19
> **mcduck said:**
> Unless the disk is formatted with a filesystem that supports packet writing (UDF, for example)  you won't be able to edit/remove individual files from it no matter if it's RW or not. Normal CD/DVD filesystem (ISO 9960) is always read-only, meaning that you can only erase and write the whole disk at a time.
good point.  So in this case, you would only be able to wipe the disk, not remove individual files.

---

### Post by swappo1 on 2009-10-19
Ok, so what program would I use to wipe the disk and then to put new files on it.  I want to back up my home drive to the disk.

---

### Post by philinux on 2009-10-19
> **ubudog said:**
> Hi, this may or may not work.  But open a terminal :Applications>Accessories>Terminal and type the following: ```
sudo nautilus
```  After that your file manager (nautilus by default) will pop up and then just select the cd from the side.  Hope that helps.:)

Please suggest ```
gksudo nautilus
```

[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)

---

### Post by philinux on 2009-10-19
> **swappo1 said:**
> Ok, so what program would I use to wipe the disk and then to put new files on it.  I want to back up my home drive to the disk.

I think k3b can do it but it's crashing on karmic so I cant test.

---

### Post by mike555 on 2009-10-19
if you want to change the content, copy it to your HD , change it , record it back to CD-rw

---

### Post by ubudog on 2009-10-19
> **mike555 said:**
> if you want to change the content, copy it to your HD , change it , record it back to CD-rw

Yes, best option. :)

---

