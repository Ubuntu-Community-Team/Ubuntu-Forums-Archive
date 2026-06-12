---
title: "Newbie RAID question"
date: 2012-05-21
forum: General Help
---

### Post by quickk on 2012-05-21
Hi everyone, 

   I'm trying to make a raid array with two new 2TB hard drives to use as my home directory before I install kubuntu.   So I booted up with the live cd, installed mdadm and created the array as such (after reading various things on the web):

```

sudo mdadm --create /dev/md1 --metadata 1.2 --level=10 --layout=f2 --raid-devices=2 /dev/sda1 /dev/sdb1 

```

I checked on the progress with cat /proc/mdstat and it says that it is going to take 1100 minutes to complete!   I read that you could use the array right away ([https://raid.wiki.kernel.org/index.php/Initial_Array_Creation]("https://raid.wiki.kernel.org/index.php/Initial_Array_Creation")) and so I was wondering: could I install kubuntu (on a different disk) right away, using the raid as home, and reboot?   Will the initial raid creation continue once my system is rebooted with the new kubuntu installation?

THanks!

---

### Post by piratebill on 2012-05-21
Raid 10 requires a minimum four drives.  You're only feeding it two.

---

### Post by quickk on 2012-05-21
> Raid 10 requires a minimum four drives. You're only feeding it two. 

That's what I used to think, but it turns out that with linux software RAID, you can do RAID 10 with only two drives.  If you specify the --layout=2 option, then you get the benefits of the same read performance as RAID 0, with minimal write penalty.   See [http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10]("http://en.wikipedia.org/wiki/Non-standard_RAID_levels#Linux_MD_RAID_10").

So does anyone know if I can install ubuntu, reboot, install mdadm and then have it continue the raid array build process from where it left off when I was using the live CD?   I imagine that for this to work, I'd have to copy over some config file.  Would this work?

---

### Post by choppyfireballs on 2012-05-21
> **piratebill said:**
> Raid 10 requires a minimum four drives.  You're only feeding it two.

^^ if you want redundancy use raid 1
works great.

---

### Post by quickk on 2012-05-21
> ^^ if you want redundancy use raid 1
works great.

Even if I just have 2 drives, using raid 10 with --layout=f2 gives me the advantage of the same read performance of raid 0 with the redundancy of raid 1.   The data is just organized a bit differently:

**raid 1**

disk1     disk2
A1        A1
A2        A2
A3        A3
..        ..


**raid 10 with f2 layout**

disk1     disk2
A1        A2
A3        A4
A5        A6
..        ..
A2        A1
A4        A3
A6        A5

So you see, both disks contain the same info.   The read performance is supposed to be almost 2X the performance of just raid 1.   At least in theory anyway!   This is my first time trying to make a raid array!

---

### Post by piratebill on 2012-05-21
> **quickk said:**
> 
So does anyone know if I can install ubuntu, reboot, install mdadm and then have it continue the raid array build process from where it left off when I was using the live CD?   I imagine that for this to work, I'd have to copy over some config file.  Would this work?

Why not just install ubuntu and then create the Raid?  Seems like less hassle (I doubt the quoted method would work.  It might, but it might not)

---

### Post by quickk on 2012-05-21
Maybe that's what I should have done.   I started with the raid array because I wanted to put /home on it, and so I was worried that installing ubuntu first would mess things up because I'd have to move /home onto the array once it was complete.   

Making the array first and then installing ubuntu gets around this, but I had no clue that it would take so long!

---

### Post by CharlesA on 2012-05-21
> **piratebill said:**
> Why not just install ubuntu and then create the Raid?  Seems like less hassle (I doubt the quoted method would work.  It might, but it might not)
That would be way easier to do. You can always move your home folder after install.

---

### Post by quickk on 2012-05-22
It worked!   I ended up just waiting the 20 hours and I just benchmarked the raid array (using palimsest).   It's definitively faster than the single drive.  

Single drive results (2TB Seagate):
[IMG]http://s17.postimage.org/5wpydfecf/2_Tb_benchmark.jpg[/IMG]

Raid array results (2x 2TB raid 10):
[IMG]http://s14.postimage.org/q0j9nwotd/raid10_benchmark.jpg[/IMG]

I couldn't benchmark the write speed for the single drive because it was already formatted.

---

