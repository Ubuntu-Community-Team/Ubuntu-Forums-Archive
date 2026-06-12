---
title: "Unable to label NTFS filesystem with GParted"
date: 2009-12-09
forum: General Help
---

### Post by mercerudy on 2009-12-09
I tried searching for this problem, but what I found only pertained to resizing the ntfs, so the solutions were to boot into another partition manager, and I don't think that will change matters for me.

I have UNR and Windows XP in different partitions.  In the "Files and Folders" tab of the netbook launcher, my Windows partition is titled "10 GB filesystem."  Since I'll probably be making another partition for another OS soon, I wanted to be able to rename or label this as "Windows Partition" or something like that.

I tried GParted, but it gave me the "Unable to read contents of this filesystem!" message in the info, and I am therefore unable to label it, although I've read that GParted should be able to do this with an ntfs.  It is not mounted.

Thanks in advance!

---

### Post by mc4man on 2009-12-09
Try this and see if you have any better luck
```

sudo apt-get install ntfsprogs
```

---

### Post by Vishnu V on 2009-12-09
install ntfs-3g

```

sudo apt-get install ntfs-3g

```

---

### Post by mercerudy on 2009-12-09
"ntfs-3g" was apparently already installed, but "ntfsprogs" did the trick

Thanks!

---

