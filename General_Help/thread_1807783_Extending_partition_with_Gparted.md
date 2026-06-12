---
title: "Extending partition with Gparted"
date: 2011-07-19
forum: General Help
---

### Post by kirill578 on 2011-07-19
Is there any way to use unallocated space to extend a partition that isn't close to that partition?
there is an image attached, I can extend /dev/sda2 but not /dev/sda1 ( the one that i want to)

I used the live cd to run gparted
[U]
I FOUND A SOLUTION:[/U]

I had to move /dev/sda2 to to the right and then extend /dev/sda1

---

### Post by wannabegeek on 2011-07-19
I don't see an attachment, but I think you can do most anything with Parted Magic.

I suspect that PM uses gparted, but has a bunch of programs added to make more combinations of changes easy for 
anybody to do. PM is also a complete OS with wifi support and a web browser, so your machine can still be used to trouble shoot or just kill time while waiting for the operations to complete.

Google Parted Magic Download.  Typically people burn the iso and run the resultant Live CD.  There are ways to use PM from a USB drive, but it may be a hassel  if not strictly required.

---

