---
title: "installing grub2"
date: 2011-04-16
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2011-04-16
so i basically transplanted some partitions and i want to make it boot-able
i would rather not start from scratch
i copied a root partition and created a home partition now i need to make it boot-able
the partition is /dev/sda1

---

### Post by pqwoerituytrueiwoq on 2011-04-17
screw it i guess i will have to install from scratch guess i will be up all night downloading everything i need on the slowest dsl money can buy <.<
it is like watching the grass grow

---

### Post by lmarmisa on 2011-04-17
I recomend to follow the method 3 chroot of this page:

[https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT](https://help.ubuntu.com/community/Grub2#METHOD%203%20-%20CHROOT)

If you have transplanted the swap partition, its UUID will be now different. You can have the same problem with UUID of the Ubuntu partition(s). I recommend to update UUIDs on the file /etc/fstab.

Best regards,

Luis

---

### Post by pqwoerituytrueiwoq on 2011-04-17
already did the fstab stuff down to the comments
i had to do it to my home partition had a hdd fail if it had only supported SMART maybe i would have known it was about to die

---

### Post by lmarmisa on 2011-04-17
> **pqwoerituytrueiwoq said:**
> already did the fstab stuff down to the comments
i had to do it to my home partition had a hdd fail if it had only supported SMART maybe i would have known it was about to die

I think you could remove the file /etc/mtab too. You can get some trouble because fstab has changed.

---

### Post by pqwoerituytrueiwoq on 2011-04-17
Thanks, you just saved me many hours of work (and downloading)
sadly it is not winter anymore i am trying to use the cold trick to get the old dead hdd to spin up so i can copy stuff off it all of it can be replaced just 2 days of downloading a game i got with a processor was at 80% *sigh*

---

### Post by lmarmisa on 2011-04-17
I wish you the best of luck in your efforts.

I recommend to use [Clonezilla]("http://clonezilla.org/clonezilla-live.php") or any other backup program. An external hard drive for storing backups is a good investment too.

Best regards,

Luis

---

### Post by pqwoerituytrueiwoq on 2011-04-17
i was planning on copying it to another disk when it finished downloading
i have copies of about everything some where
music on ipod/laptop
Firefox settings on laptop
i have a usb hdd
this is the second time i had a disk die on me 1st time it was not my fault
made in china power cord was not as one was as it should have been...
the hdd was covered under warranty in that case :)

this one is not even spinning up it is done for my other dead one probably needs a new circuit board

---

