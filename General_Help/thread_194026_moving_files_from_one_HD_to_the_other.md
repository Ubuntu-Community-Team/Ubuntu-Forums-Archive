---
title: "moving files from one HD to the other"
date: 2006-06-10
forum: General Help
---

### Post by Therrol on 2006-06-10
I just got myself a new 30gb HD to replace the 10 gig, and I want to move my linux partition (single partition) over to the 30 gig and resize it to take up the full drive. I then want to install windows on the 10 gig.

How would I go about doing it?

---

### Post by scxtt on 2006-06-10
your new HDD should have come w/ (or you can d/l it from the manu. site) some software that will allow you to copy partitions b/t drives (might only work b/t drives of the same manu.? - i.e. you boot from the CD and work w/ the 2 drives from the interface the CD gives you - a la W.D.'s Dr.Dos) ... you'd probably have to do something to either reset the MBR (windows) or reinstall grub (*nix) to be able to boot off them ... tho i'm sure you can specify loading windows into grub by editing your menu.lst ...

---

### Post by Therrol on 2006-06-10
sorry, I should have mentioned that this drive is only "new" to me, its a used drive.

---

### Post by aysiu on 2006-06-10
[http://www.psychocats.net/ubuntu/partimage.html](http://www.psychocats.net/ubuntu/partimage.html) will help you move over the Linux partition. Then, after you install Windows, you should [restore Grub to the MBR](http://ubuntuforums.org/showthread.php?t=24113) so you can dual-boot.

---

