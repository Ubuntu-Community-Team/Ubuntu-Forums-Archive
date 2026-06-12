---
title: "changing boot partition to the copied one"
date: 2009-10-14
forum: General Help
---

### Post by ioasw on 2009-10-14
I'm on Ubuntu Jaunty -and-
 
I used Gparted to shrink my windows partition down to make room for an expansion of my Ubuntu partition. I ran the live CD and went into Gparted and it will not let me extend or merg my ubuntu partition with the unformatted or formatted free space that was left after the shrinking of the windows partition. If anyone knows how I can simply merg or extend my Ubuntu partition that would be best for me, but what I've done so far is copied my Ubuntu partition to the larger partition left over from the windows shrink, and now ubuntu cannot mount the volumne. I was hoping I could jsut switch the boot partition to the larger volumne. I've read through serveral posts on the web, and I cannot seem to fix the problem is there are better app then Gparted? I've tried modifying the partitions with windows Acronis Disk Director and I don't get anywhere either. I'm thinking about just waiting for 9.10 and then doing a fresh install, but the installation of the drivers was a pain I don't want to do that again unless I have to.
 
thanks for any help!

---

### Post by ioasw on 2009-10-14
This is what my Gparted looks like:

[http://picasaweb.google.com/lh/photo/t4rSWFyV-VUKMVcIzVDlvQ?feat=directlink]("http://picasaweb.google.com/lh/photo/t4rSWFyV-VUKMVcIzVDlvQ?feat=directlink")

I would like to merge the 29.29GB partition which is my boot partition with the 144.48 partition.  Gparted will not let me do it even under the live CD boot.  The 29.29GB partition does not allow for expansion or growing.

---

### Post by mechro on 2009-10-14
You've made some sort of mess when copying Ubuntu to what is now /dev/sda4. What method did you use to copy?

A possible solution...

In LiveCd/Gparted...

1) Delete /dev/sda4

2) Extend /dev/sda3 to fill from end of /dev/sda2 to end of drive.

3) Extend /dev/sda5 to fill from end of /dev/sda2 to end of drive.

---

### Post by ioasw on 2009-10-14
Thanks mechro it worked.  I was leaving out your second step, I didn't think I had to extend sda3 before sda5, GREAT!  This is a great note to anyone having troubel doing this. 
 
ALSO NOTE: I had to reboot into the live CD again after the above steps and check sda5 because there was an error with the first attempt, but after that it worked perfectly.
 
Maked SOLVED please!

---

