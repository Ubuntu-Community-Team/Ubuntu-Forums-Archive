---
title: "Partition rezising ended up bad."
date: 2009-10-02
forum: General Help
---

### Post by boubbin on 2009-10-02
Hey,

I used live-cd and gparted to resize couple of my partitions.
It all went smooth, until the resizing freezed Gparted! It was moving the parition to right while it happened and the operation got at 88%. I was moving my /home/ at that time.

When i boot up Ubuntu everything seems fine, but when i try to access some of the files i got "EXT3-fs error (device sda3) ext3_readdir #NUMBERS_HERE contains hole at offset OTHER_NUMBER_HERE"

I have been trying to fix this with "recovery mode" and fsck, fsck finds ALOT of problems to fix! I left my cellphone on the ENTER and it went on like multiple hours... and it still keeps finding errors in there.

What should i do?
I got some really important information there that i would like to save.

---

### Post by boubbin on 2009-10-02
ok it seems ok now.
i runned: fsck -C -V -f -y
and it went really fast and fixed everything! Seems ok now!

---

### Post by Giblet5 on 2009-10-02
> **boubbin said:**
> ok it seems ok now.
i runned: fsck -C -V -f -y
and it went really fast and fixed everything! Seems ok now!

Uh huh...

You have a backup, just in case, right?

---

### Post by boubbin on 2009-10-02
actually i dont :)
but for now on i will definitely have!

---

### Post by boubbin on 2009-10-03
this thread can be marked as [solved]

---

