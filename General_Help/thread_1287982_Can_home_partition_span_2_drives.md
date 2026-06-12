---
title: "Can home partition span 2 drives?"
date: 2009-10-10
forum: General Help
---

### Post by KayakJim on 2009-10-10
I have 2 drives in my system - a 64GB SSD and a 320GB HD.

My ubuntu setup does not need 64GB of space so I would like to have my /home partition occupy 24GB of the SSD along with the entire 320GB drive.

Is this possible for my /home partition to span 2 drives and if so how?

---

### Post by Boondoklife on 2009-10-10
I believe it is possible with LVM as that will allow you to have the partition across multiple places.

---

### Post by CatKiller on 2009-10-10
There are ways to do it, but you might find it easier to just have your static data on a partition that spans the larger drive and simply have that accessible from your Home folder. Either by mounting it to /home/*username*/data, say, or by mounting it to somewhere like /mnt/data and then symlinking appropriate directories from that location to ~/Pictures or ~/Music, or what-have-you. Effectively having 320GB of data and 24GBs of configuration files available.

---

### Post by jerome1232 on 2009-10-10
As bond pointed out LVM allows you to do this. Using the Alternate install cd makes it very easy to setup LVM.

You would do your root partition and swap normally, then set the rest of the ssd as a physical volume for LVM, do this for the other disc as well.

Make 1 volume group which uses both of those physical volumes.

Create 1 logical volume inside that volume group and let it take all the free space.

Let the install roll along.

---

### Post by Johnny B on 2009-10-10
you could just do it the lazy way and just mount the 320gb drive inside /home

---

