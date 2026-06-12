---
title: "boot problem"
date: 2006-04-07
forum: General Help
---

### Post by evillawngnome on 2006-04-07
grub appears to do its thing, it says:
Decompressing linux.....Ok, booting the kernel
ANd then nothing happens.

Everything WAS working fine. I had this prototype PC running without a case, just parts + power supply laying on the work bench and it worked for over a week. Now that i get it in the case, it doesnt want to play nice.

---

### Post by taurus on 2006-04-07
I would recommand you check all the wires and connections to make sure nothing is lose...

---

### Post by evillawngnome on 2006-04-07
CHecking that now.
Just out of curiousity, in the previous configuration, i had more drives on one of the SCSI channels, and due to space limitations, i had to remove them. Would that make a difference?

---

### Post by nanotube on 2006-04-07
it might, if grub is now looking for stuff on the wrong disk, due to change in drive order...

---

### Post by Sutekh on 2006-04-07
[QUOTE=evillawngnome]Just out of curiousity, in the previous configuration, i had more drives on one of the SCSI channels, and due to space limitations, i had to remove them. Would that make a difference?[/QUOTE]
Yes this could have made all the difference.  SCSI devices seem to change their device location (/dev/sd#) quite easily.  The removal of some could cause GRUB to become unable to find the correct drive to boot the kernel.

Oh nanotube has already suggested that. (too slow)

---

### Post by evillawngnome on 2006-04-07
Okay, more fiddling has yeilded this:
It will boot, it just takes HOURS. Or it would, if i had the patience to let it go.
Also, i was very careful to keep the SCSI things neat and tidy; the drives i removed were on channel C, and the boot device was on channel A. It was /dev/sda before, and as far as i know, it still is.

---

