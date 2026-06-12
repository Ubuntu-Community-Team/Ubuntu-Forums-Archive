---
title: "Contents 3.2GB, 3.6GB used, where does the extra 400mb come from?"
date: 2010-09-09
forum: General Help
---

### Post by MadnessRed on 2010-09-09
If I right click on my Memory card in Nautilus and select Properties, I get the following information:

Type: folder (inode/directory)
Contents: 8,038 items, totalling 3.2 GB

Location: computer:///
Volume: 4.0 GB Filesystem

Free space 198.4MB
3.6 GB used
198.4 MB free
Total capacity: 3.8 GB
Filesystem type: msdos


I get that the 4.0GB is a label and you never get the full capacity, hence why it is only 3.8GB.

My problem though is with the total filesize.
If I have 3.2GB of files, why is 3.6GB of the card used?
And can I get that 400mb back anyway? It would tripple the free space on the card if I could.

Any help would be great.

MadnessRed

---

### Post by zuerston on 2010-09-09
I had that same problem with my 4gb HP stick, and I fixed it with a new 8gb stick.

---

### Post by theozzlives on 2010-09-09
MSDOS file system is way outdated. Try backing up your data and re-format to ntfs. Also, on Microsoft file systems, you have to defrag once and awhile.

---

### Post by MadnessRed on 2010-09-09
> **zuerston said:**
> I had that same problem with my 4gb HP stick, and I fixed it with a new 8gb stick.

Yh, I am looking into an 8gb stick, there are much cheaper than they used to be.

Where does that extra 400mb go though? I had a 270mb file, and when I deleted it, I had 190mb free on the card. So some of it went there, but that still doesn't explain anything or account for the rest of the missing space.

---

### Post by MadnessRed on 2010-09-09
> **theozzlives said:**
> MSDOS file system is way outdated. Try backing up your data and re-format to ntfs. Also, on Microsoft file systems, you have to defrag once and awhile.

it's a phone memory card, so I don't really want to reformat as apparently that can cause problems. In windows it is shown as FAT32. I am defragmenting it now, even though windows said it wasn't needed.

---

### Post by Jesus_Valdez on 2010-09-09
Have you empty the Trash folder of the card?

there must be a hidden folder on the root folder of the card.

---

### Post by zuerston on 2010-09-09
I think all those cards and sticks and even hard drives have a small "private" space that they keep their own secret info in.
I once did manage to delete it somehow with a utility program and it would never work again,so I don't worry about it no mo.

---

### Post by theozzlives on 2010-09-09
It's not wise to use your SD card as a flash drive. I'd suggest backing up the card and let your phone format it. Restore and you should be fine. Use your phone to delete files. If you have a USB cable, then copy files using Mass Storage mode on your phone.

---

### Post by MadnessRed on 2010-09-09
> **Jesus_Valdez said:**
> Have you empty the Trash folder of the card?

there must be a hidden folder on the root folder of the card.
Nope, no hidden folders, at least none discoverable by Control+H and I remove the .TRASH folder regularly

> **zuerston said:**
> I think all those cards and sticks and even hard drives have a small "private" space that they keep their own secret info in.
I once did manage to delete it somehow with a utility program and it would never work again,so I don't worry about it no mo.

I though that was taken into account already though, hence why it shows 3.8 not 4.0gb.
Also I deleted a 200mb+ file and had less than 200mb free afterwards. And I removed the .trash folder. And idea where the space could have gone?



> **theozzlives said:**
> It's not wise to use your SD card as a flash drive. I'd suggest backing up the card and let your phone format it. Restore and you should be fine. Use your phone to delete files. If you have a USB cable, then copy files using Mass Storage mode on your phone.

Thats what I am doing.

---

### Post by vert11 on 2010-09-09
according to me it is the space occupied by the "filesystem tables" where it keeps the locations or pointers to the blocks of memory....

---

