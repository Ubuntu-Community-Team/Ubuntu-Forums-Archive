---
title: "Partition order"
date: 2012-03-15
forum: General Help
---

### Post by rmcellig on 2012-03-15
I am going to reformat my laptop and create three partitions (swap, system, documents). Does it matter which order these partitions are created? In other words, does the swap partition go at the beginning of the drive followed by the system partition and then the documents partition?

---

### Post by Dngrsone on 2012-03-15
It does not matter.

---

### Post by Bucky Ball on 2012-03-15
It doesn't matter but the old rule of thumb was to put OS first and /swap last (but drives are faster now). I generally have:

/
/home
/swap

In your case, this would equate to:

/ = system; 20Gb plenty;
/home = 'documents' as there is already a documents directory (along with others) in there and you make this partition large as you like;
/swap = 2Gb fine.

You can put them where you like but it makes it a lot easier if you have some uniformity (especially when working with your partitions or reinstalling). Maybe its just me but when it comes to partitioning I always have a plan so I don't get confused later. ie: I have four machines and it is much easier to have them all partitioned the same rather than partitions dumped on wherever so I have to figure what's where whenever I'm working on a particular machine. This is even more relevant if you were working with fifty of the buggers! ;)

---

### Post by Helen McCall on 2012-03-18
The old rule of thumb used to be that the fastest seeks on a disk would be those around the middle of the disk. I am assuming that this is still the case with modern drives.

Therefore you want to put the swap partition between your other two partitions so that you get the fastest seeks when using swap memory.

So it would be:

/
swap
/home

Also it is advisable to make the swap space at least as large as the physical ram you have. I tend to make my swap spaces 20Gig these days because disk space is cheap and you don't want to ever run out of swap space.

The root (/) partition needs to be large enough to accumulate /tmp and /var files as well as all the packages you install. I would advise around 50Gig if you have a modern large disk.

---

### Post by rmcellig on 2012-03-18
I formatted my drive on my test laptop as follows:

/swap 3GB
/ 17GB
/home /175GB

I guess I can move the swap partition in the middle with Gparted . So I should also resize the partitions based on your answer? I have 3GB of physical RAM. Thanks for your reply!

---

### Post by Bucky Ball on 2012-03-18
> **Helen McCall said:**
> The old rule of thumb used to be that the fastest seeks on a disk would be those around the middle of the disk. I am assuming that this is still the case with modern drives.

Therefore you want to put the swap partition between your other two partitions so that you get the fastest seeks when using swap memory.

So it would be:

/
swap
/home

Also it is advisable to make the swap space at least as large as the physical ram you have. I tend to make my swap spaces 20Gig these days because disk space is cheap and you don't want to ever run out of swap space.

The root (/) partition needs to be large enough to accumulate /tmp and /var files as well as all the packages you install. I would advise around 50Gig if you have a modern large disk.

Sorry to disagree with all of this. ;)

The fastest part is the outside of the platter and you want your DATA and OS read fastest, NOT the /swap which is very rarely used, and generally when it is, it is for hibernation ... therefore, in a one drive setup you want your OS on the first partition. 

See the basic setup I originally suggested in post #3.

For AV work, you always have a separate data drive so the recorded (and played back) data goes on the fastest part of the drive; first partition, which will be on the outside edge of the platter working in, before even the OS (because the OS is on another drive). 

Moving your partitions around (shrinking/deleting/expanding/creating) MUST be done using the LiveCD as all the partitions you are intending to work on must be unmounted; obviously not possible if your OS is running from the partition you are resizing.

The way the OP has it setup now (partition sizes) is just fine. But I'd stick the /swap at the end, thus:

* Delete /swap
* Expand / into the free space
* Shrink /home by 2Gb
* Create /swap in the free space

Done, giving you a virtually identical setup to that suggested in post #3. ;)

PS: /swap is rarely used because of the amount of RAM used now; 20Gb is WAY to much. (/swap is used mostly for hibernation; if you have 20Gb of data in your RAM when you close the laptop lid or otherwise go into hibernation, presuming you have 20Gb of RAM, then maybe you'll need 20Gb /swap. 2Gb is generally fine. ;)

PPS: In the end it's all a bit superfluous; doing it this way is just how it's been done for ages. With 7200rpm hard drives and beyond, unless you are doing hard-core AV work, you are really not going to notice the difference regardless where you put 'em! The convention is mostly to prevent confusion. Same when you look at Windows machines. OS first, data second. Pagefile (=/swap), as with Ubuntu, you can put anywhere also, on another drive if you like for the ultimate speed! Hardly worth the effort unless there's heavy lifting required.

---

### Post by rmcellig on 2012-03-18
Thanks. I am using a single internal 250GB drive on my test laptop to try all of this stuff out.

---

### Post by Helen McCall on 2012-03-18
> **Bucky Ball said:**
> Sorry to disagree with all of this. ;)

The fastest part is the outside of the platter and you want your DATA and OS read fastest, NOT the /swap which is very rarely used, and generally when it is, it is for hibernation ... therefore, in a one drive setup you want your OS on the first partition. 


You have completely misunderstood, Bucky Ball. The governing factor in speed here (especially for an old 72000 rpm drive) is the seek time to find data to read. The seek times are quicker in the centre of the platter than on the outside. Therefore if you want fast access to swap you put it in the middle.

> **Bucky Ball said:**
> PS: /swap is rarely used because of the amount of RAM used now; 20Gb is WAY to much. (/swap is used mostly for hibernation; if you have 20Gb of data in your RAM when you close the laptop lid or otherwise go into hibernation, presuming you have 20Gb of RAM, then maybe you'll need 20Gb /swap. 2Gb is generally fine. ;)


The use of swap space is nothing to do with hibernation. The swap space usage depends heavily on the way in which the user is using the computer. With Unix/Linux systems, users tend to multi-task more than ever happens on windows machines. Swap space is still used a lot when needed. Take a look at all the threads on these forums where people are complaining about system freezing, and the4 many answers telling them to check that they have enough swap space. I do video editing on my machine and this is one of the reasons why I go over the top with 20GB, but rmcellig's choice of 3GB is a better option than your 2GB limit.

Likewise the root partition needs to have sufficient space to take all the /var and /tmp files. The disk described by rmcellig seems rather small, but I would make the root larger if possible because the 17GB can be easily filled depending on what packages are installed. With 17GB you need to clear out caches such as the cache of downloaded packages at intervals if installing a lot of software.

The advice I have been giving on here is aimed at reducing the chance of a system freeze or lockup due to insufficient resources being available.

---

