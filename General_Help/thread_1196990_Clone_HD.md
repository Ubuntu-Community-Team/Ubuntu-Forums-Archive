---
title: "Clone HD"
date: 2009-06-25
forum: General Help
---

### Post by gletob on 2009-06-25
So I have 2 HDDs:
/dev/sda 120 Gb in laptop (Partion map attached)

/dev/sdb 320 Gb in WD My Passport

I've got the WD completely blanked

I want my current partion scheme moved to the WD 

BTW they're both 2.5 inch sata drives.

---

### Post by Scotty Bones on 2009-06-25
This might be of some use to you
[http://www.clonezilla.org/](http://www.clonezilla.org/)

---

### Post by rbc on 2009-06-25
sudo dd if=/dev/sda of=/dev/sdb

This is going to have to be done from a LiveCD, so that none of the partitions are mounted. and it will take a while to copy. Then use gparted to do whatever you want with the free space.
This is the way I do it. There are other options, such as clonezilla and partimage. I have never spent enough time to figure them out, but there both supposed to be very easy to use. Also, be very careful to get the if(input file) and of(output file) correct. Accidentally reversing them will be disastrous.

---

