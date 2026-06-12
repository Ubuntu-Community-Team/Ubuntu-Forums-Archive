---
title: "Tevion / Medion webcam 0c45:60fe"
date: 2006-05-13
forum: General Help
---

### Post by waster on 2006-05-13
Hello,
Does anyone have any experience with this webcam:

Tevion / Medion webcam, USB ID is 0c45:60fe
It also has a manufacturer's ID of 85081 
The chipset appears to be Microdia, as reported by lsusb.

[www.linux-projects.org](www.linux-projects.org) appears to support a similar range of USB ids, but not that one. Their work is part of the kernel tree, but n.b. Ubuntu is on version 1.24, while the project has released 1.31.

Grepping the latest linux source tree doesn't give any useful matches for that USB ID.

Jack

---

### Post by rob martin on 2006-05-13
I just bought one of these from my local Aldi today, I had high hopes of it *just working* given Dapper's progress to date.  It doesn't :(  Any help would be appreciated before I take it back to the shop and have the checkout assistant explain to me that it works perfectly on their windows system, and that I must be doing something wrong ;0

---

### Post by waster on 2006-05-15
I've been in touch with the kernel modules maintainer for that type of chip. From the developer:
"it looks like it's neither sn9c101 nor 2 nor 3.
The open source driver will support sn9c105 soon.
By looking at the ids, the webcam does seem to mount a
chip from sonix, but you need to know the model of the
chip in the .inf file from the windows driver.."

---

### Post by waster on 2007-01-27
[www.linux-projects.org](www.linux-projects.org) now has released an updated kernel module which will work with a 2.6.19 or greater kernel (i.e. Feisty or home-grown). However, for my particular webcam, the chip and bridge combination isn't yet supported, but many more webcams should work with this code. Hope it can be patched into the mainline kernel or ubuntu's version.

---

