---
title: "thumbdrive raid"
date: 2010-05-06
forum: General Help
---

### Post by P4man on 2010-05-06
I want to try something *really* silly this weekend. Just for the heck of it.
My brother was given many dozen branded 2GB USB sticks to hand out to customers as a gift. I wondered if I could borrow them to set up a thumbdrive raid 5 :D

I realize USB bus is limited to ~40MB/s, my PC seems to have only 1 USB2 root controller (with 6 or so ports), but I have another PCI USB2 controller laying around somewhere which I think (hope) has 2 root hubs, So in theory I might be able to get a total of 120 MB/s combined USB bandwith (which I believe is about the limit for PCI anyway). Each stick does 20MB read and 5MB write (they are cheap sticks obviously), so Ill slap in .. ah, well, hubs permitting, 10 or 20 or so sticks LOL.

Anyway, questions:

Is raid 5 a good idea? I dont expect it to be faster than raid 0, but with that many sticks, it seems like a better idea to have some redundancy. But I have no idea how negatively it impacts performance (my cpu is a rather humble ~2 GHz core2 duo).

Ive never set up a (soft)raid. Any tips or tutorials to do this on lucid? Do I need the alternate cd? Or do I set up the raid form my current install and then install Ubuntu to it?

---

### Post by VeeDubb on 2010-05-06
RAID 5 is slightly slower than 0, the but not realy enough to notice in what you're doing.  The bottle neck will still be your USB controllers and pci bus.

As far as having a little redundancy, why bother?

I would assume that this is just a boredom/curiosity driven project and you have no intentions of doing this as a means of real storage.

---

### Post by P4man on 2010-05-06
Ill go with raid 5 just for the heck of it and see how it works. this setup isnt going to break any performance records anyway, but it would be nice to get near SSD performance (and capacity) for free ;)  

Anyay  I just wondered if it would choke my cpu, seeing 3 drive raid 5s already have a significant cpu load, doing it with 10 or 20 will probably not help. But Ill find out and report my findings :)

I just found another PCI USB2 controller card btw, so Ill have plenty root hubs to saturate my PCI bus (unless the onboard controller is hooked up via PCI-E but thats probably not the case :( )

---

### Post by P4man on 2010-05-06
Did some quick testing with just 3 sticks connected to a single USB channel.

One stick, no raid:

[[img]http://www.ubuntu-pics.de/thumb/57757/screenshot_flash_drive_sm_usb20__flash_drive_sm_usb20______benchmark_X40KPc.png[/img]](http://www.ubuntu-pics.de/bild/57757/screenshot_flash_drive_sm_usb20__flash_drive_sm_usb20______benchmark_X40KPc.png)

Avg read:  19.8 MB/s
Avg write: 4.6 MB/s
access time: 0.7ms

3 sticks in RAID 0:

[[img]http://www.ubuntu-pics.de/thumb/57758/screenshot_6_0_gb_raid_0_array__6_0_gb_raid_0_array______benchmark_jBVe3M.png[/img]](http://www.ubuntu-pics.de/bild/57758/screenshot_6_0_gb_raid_0_array__6_0_gb_raid_0_array______benchmark_jBVe3M.png)

Avg read:  40.6 MB/s
Avg write: 10.7 MB/s
access time: 0.8ms

3 sticks in RAID 5:

[[img]http://www.ubuntu-pics.de/thumb/57759/screenshot_4_0_gb_raid_5_array__4_0_gb_raid_5_array______benchmark_85bfmk.png[/img]](http://www.ubuntu-pics.de/bild/57759/screenshot_4_0_gb_raid_5_array__4_0_gb_raid_5_array______benchmark_85bfmk.png)

Avg read:  41.4 MB/s
Avg write: 7.5 MB/s
access time: 0.9ms

CPU load is neglectable so far. Looks promising!

---

### Post by VeeDubb on 2010-05-06
The raid0 to raid5 comparison looks pretty reasonable to me.  Not a significant difference in read speeds, but a little chunk lost on the write speeds.

I'll be curious to see what happens when you've stuck 20 USB sticks in there.  I still suspect that once you go past the reasonable limits of the busses involved, you'll stop seeing any difference between 0 and 5.

---

### Post by P4man on 2010-05-06
If by then the CPU doesnt become a bottleneck..

Im only getting a batch of 10 sticks though :(. Think I have 4 or 5 comparable (or faster) sticks floating around the house, so Ill aim for 4 sticks per usb controller for 12 total.

BTW is it possible to "nest" raids? Like creating 3 stripe sets of 4 sticks each and arranging those in raid 5 or 5 sets in 5 raid  each set consisting of 2 sticks in raid 1?

---

### Post by P4man on 2010-05-06
Picked up my sticks :D

Just tested with only 1 usb controller, I attached 12 sticks using 2 hubs and front panel. My desk is lit up like a Christmas tree lol. 

Scaling clearly isnt anything like linear, and I seem to have maxed out on read throughput long ago, write performance seems to go up still, although not as much as I had hoped (and expected):

12 sticks 1 USB controller RAID 0

[[img]http://www.ubuntu-pics.de/thumb/57818/12_sticks_1_usb_raid_0_v7dD9u.png[/img]](http://www.ubuntu-pics.de/bild/57818/12_sticks_1_usb_raid_0_v7dD9u.png)

Avg read: 41.8 MB/s
Avg write: 19.4 MB/s
access time: 0.7ms

12 sticks 1 USB controller RAID 5

[[img]http://www.ubuntu-pics.de/thumb/57819/12_sticks_1_usb_raid_5_larYFI.png[/img]](http://www.ubuntu-pics.de/bild/57819/12_sticks_1_usb_raid_5_larYFI.png)

Avg read: 41.6 MB/s
Avg write: 15.2 MB/s
access time: 1.1ms

CPU load is still rather low, ~15%

Ill toss in 2 other USB controller shortly and add a few more sticks, see if that helps.

---

### Post by P4man on 2010-05-06
Well, for some reason my PC would not work with 2 identical PCI USB cards. One or the other worked fine, when I inserted both, only 1 was recognized. But it doesnt look like 2 would have helped anyway.

The setup:

[[img]http://www.ubuntu-pics.de/thumb/57893/usbsticks_ZuK0no.jpg[/img]](http://www.ubuntu-pics.de/bild/57893/usbsticks_ZuK0no.jpg)

4 more sticks in the back of my PC :)
many thanks to Juniper Networks for supplying me with the sticks :p

An unusual sight:

[[img]http://www.ubuntu-pics.de/thumb/57894/raid_Vt4iP1.png[/img]](http://www.ubuntu-pics.de/bild/57894/raid_Vt4iP1.png)

15 sticks in Raid 0 over 2 USB controllers:

[[img]http://www.ubuntu-pics.de/thumb/57898/15x2_raid_0_f01oo5.png[/img]](http://www.ubuntu-pics.de/bild/57898/15x2_raid_0_f01oo5.png)

Avg read: 46.1 MB/s
Avg write: 21.6 MB/s
access time: 0.8ms

I have no idea where the bottleneck is. But I guess SSDs have their place :D

15 sticks in Raid 5 over 2 USB controllers:

[[img]http://www.ubuntu-pics.de/thumb/57902/15x2_raid5_6TZoF5.png[/img]](http://www.ubuntu-pics.de/bild/57902/15x2_raid5_6TZoF5.png)

Avg read: 45.9 MB/s
Avg write: 16.8 MB/s
access time: 1.1ms


You can buy 16/32GB thumbdrives with nearly the same performance. So I guess its as pointless as I thought it would be, but hey, someone had to test it :D

---

### Post by VeeDubb on 2010-05-06
> **P4man said:**
> BTW is it possible to "nest" raids? Like creating 3 stripe sets of 4 sticks each and arranging those in raid 5 or 5 sets in 5 raid  each set consisting of 2 sticks in raid 1?

I know it's possible to nest 0 inside of 1, which is refered to as Raid 1+0 or Raid 10, but I'm not sure about 0 and 5.

---

