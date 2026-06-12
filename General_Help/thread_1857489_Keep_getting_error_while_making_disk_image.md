---
title: "Keep getting error while making disk image"
date: 2011-10-10
forum: General Help
---

### Post by pretty_whistle on 2011-10-10
I did this fine just yesterday but now Clonezilla tells me "partition is broken OR cannot be checked" (I set it to check image for integrity).

I've tried making a disk image several times but the same issue appears.  

Hoping to solve it I've tried deleted the trash using gksudo. I've tried deleting off an image saved about 4 days ago to make more space (not that it needed it!). I've tried unplugging the portable drive (where the images are saved to) and restarting the computer.  I tried restarting the computer several times.  Nothing has worked.

What is going on??  When using the computer everything appears ok.

I have Ubuntu 11.04.

---

### Post by pretty_whistle on 2011-10-10
Is there another free program I can use to make disk images since this one is failing?

---

### Post by 2F4U on 2011-10-10
From where do you attempt to create the image, from a liveCD?

---

### Post by pretty_whistle on 2011-10-10
> **2F4U said:**
> From where do you attempt to create the image, from a liveCD?
Yes.

---

### Post by pretty_whistle on 2011-10-10
Solved.  Here's how:

Clonezilla has fsck option in advanced mode so I checked it and it ran and solved the issue.  In Clonezilla it appears as:

> -fsck-src-part



One hint this was needed was getting this error message while trying to make a disk image:

> sda3 was mounted XXXX times and not checked

(where XXXX is a number)

---

