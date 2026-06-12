---
title: "Adding old ubuntu partion to C:"
date: 2009-07-17
forum: General Help
---

### Post by akrchstn on 2009-07-17
I uninstalled ubuntu because I am going to put it on an external hard drive. So I went to manage my computer, deleted the ubuntu partion, popped in my windows 7 install cd, went to command prompt and put in bootrec.exe /fixmbr then put in my ubuntu live cd, went to gparted and i got whats in the picture. There is no option for me to add the unallocated space back to my primary drive and I don't want to have an extra drive.

---

### Post by merlinus on 2009-07-17
That is because the unallocated space is within an extended partition.  Try deleting sda2.

---

### Post by akrchstn on 2009-07-17
It worked, thanks merlin

---

### Post by merlinus on 2009-07-17
Excellent news!  Have fun, and post back if you run into other difficulties.

---

