---
title: "Partition size?"
date: 2012-07-09
forum: General Help
---

### Post by t0p on 2012-07-09
I just bought myself a new laptop.  It came with Windows 7, which I've decided to keep (why the heck not?  I paid for the damn thing...) and I want to set up a dual-boot thing, Windows 7 and Ubuntu 12.04 (64 bit version).

So, I've got to wondering: what size partitions should I create on the HDD?  How many Gigs for Winders, how big the swap, and how many Gigs for Ubuntu?  I realise this is a kinda personal question, with various correct answers, but I've posted this to get a feel for the thing.

I'll also ask: is a dual-boot the right way to go?  Maybe I should install VirtualBox on my existing Windows7. and create a *virtual* Ubuntu?

So what am I going to use the laptop for?  Web browsing, email, playing backgammon and freedoom, managing and editing photos (I got Photoshop Elements bundled on it.  I've always used Gimp for that kinda stuff, but I've heard/read so much good stuff about Photoshop so I gotta try it out, y'know?)

Okay, the lappy's specs: it's a Packard Bell Easynote TS13-HR-823UK, Intel Celeron Dual-Core, 6GB RAM, 500GB HDD.

Opinions please?  Cheers!

---

### Post by Basher101 on 2012-07-09
For Windows 7 60-80 GB should be plenty for programs, updates and other stuff. (if you can keep software low, 50 GB will suffice.)

For Ubuntu 20-40 GB should be enough and your SWAP should be as big as your RAM.

I would recommend a dualboot instead of a virtualbox on Windows, as Windows will get sluggish over time.

The rest of the space, well, on my part i use 80% of my HDD for a shared storage between both Operating systems. I made rather small partitions for the OSs to make Backups and Rollbacks much quicker and painless.

this is my advice so far


peace

---

### Post by papibe on 2012-07-09
Hi t0p.

Quick thoughts:

Windows 200G-250G (the last if you plan to install games).

My rule of thumb for Ubuntu:
```

/      15-25Gb
swap   match your RAM (to support hibernation).
/home  all the rest
```
Hope it helps.
Regards.

---

### Post by Mark Phelps on 2012-07-10
If you plan on sharing data files a lot between Windows and Ubuntu, I'd go with the lower Win7 size (50GB) and create a shared NTFS data partition; otherwise, the larger size (250GB)would be better.

---

### Post by Hydera5 on 2012-07-10
Hello, I'm new to the Ubuntu community.  I have a 750GB HDD w/ windows 7.  I have run Ubuntu on my 16GB flash drive (The external flash drive makes it hard/risky for carry and the lack of space is concerning) and as well as in Vertualbox and VMware player(while okay not suitable for me)I was wanting to know an answer for a few questions I have.

1.  what filesystem should the format be for Ubuntu?

2.  If I wanted to share files between the 2 OS' Would I have to shrink the windows partition, add an Ubuntu partition, **AND** create a 3rd for the OS' to share?  Or could I have one Windows partition and one Ubuntu and be able to share between the two without the need for the 3rd partition?

3.  If for whatever reason I want to remove Ubuntu and the partition it was on, can I do so without affecting the partition that has windows on it (in terms of data loss and corruption)?

The help is greatly appreciated!

---

### Post by papibe on 2012-07-10
> **Hydera5 said:**
> 1.  what filesystem should the format be for Ubuntu?

I would recommend ext4.

> **Hydera5 said:**
> 2.  If I wanted to share files between the 2 OS' Would I have to shrink the windows partition, add an Ubuntu partition, **AND** create a 3rd for the OS' to share?  Or could I have one Windows partition and one Ubuntu and be able to share between the two without the need for the 3rd partition?

Accessing Windows files from Ubuntu won't require anything special. The other way around will.

Yes, a 3rd NTFS partition would do the trick.

> **Hydera5 said:**
> 3.  If for whatever reason I want to remove Ubuntu and the partition it was on, can I do so without affecting the partition that has windows on it (in terms of data loss and corruption)?
It shouldn't be a problem, although removing a OS is always a delicate task. The worst case scenario is that you temporary loose the ability to boot in Windows (if you remove grub). But that can be easily fix with the Windows' restore CDs.

Hope it helps.
Regards.

---

### Post by Rebelli0us on 2012-07-10
Don't screw around with partitions, you risk making your computer unbootable. Just run Linux in a VirtualBox virtual machine, you'll find it in Ubuntu Software center.

---

### Post by Hydera5 on 2012-07-10
> **Rebelli0us said:**
> Don't screw around with partitions, you risk making your computer unbootable. Just run Linux in a VirtualBox virtual machine, you'll find it in Ubuntu Software center.

Could you explain a little more?  If I am understanding you correctly, even if I have the windows install disk, I can still risk not being able to load another OS onto the machine? (I would only encounter this problem when Ubuntu is removed incorrectly, is that correct?) 

Plus the VM has its bugs some times,  Also if I decide I need more space it is a pain to extend a .vmdk

I was looking into dual booting but if you seriously don't recommend it, I guess I can make the VM work...

Thanks

---

### Post by Rebelli0us on 2012-07-10
> **Hydera5 said:**
> Could you explain a little more?  If I am understanding you correctly, even if I have the windows install disk, I can still risk not being able to load another OS onto the machine? (I would only encounter this problem when Ubuntu is removed incorrectly, is that correct?) 

Plus the VM has its bugs some times,  Also if I decide I need more space it is a pain to extend a .vmdk

I was looking into dual booting but if you seriously don't recommend it, I guess I can make the VM work...

Thanks


There are countless posts in this forum where people can no longer boot. Partitioning is not for novices.

VMs work just fine, and you don't need to reboot, you can run both OSes simultaneously.

---

### Post by Hydera5 on 2012-07-10
> **Rebelli0us said:**
> There are countless posts in this forum where people can no longer boot. Partitioning is not for novices.

VMs work just fine, and you don't need to reboot, you can run both OSes simultaneously.

As of now the only thing I see as a downside of doing this is RAM and cores.  I have an i7 and 8 GB of RAM.  As of now i have 4 out of 8 cores running Ubuntu and I give it about 3.5GB of RAM.  What do you recommend for my setup.  (I want it to be as smooth as it can, but at the same time if it crashes I dont want Ubuntu to bring the host OS down with it!)

Also how much HDD space should I give it?  Could you point me to a site that will show me how to increase the .vmdk file if I run out of space in the future?

Thanks for putting up with me Rebelli0us :P

---

### Post by Rebelli0us on 2012-07-11
> **Hydera5 said:**
> As of now the only thing I see as a downside of doing this is RAM and cores.  I have an i7 and 8 GB of RAM.  As of now i have 4 out of 8 cores running Ubuntu and I give it about 3.5GB of RAM.  What do you recommend for my setup.  (I want it to be as smooth as it can, but at the same time if it crashes I dont want Ubuntu to bring the host OS down with it!)

Also how much HDD space should I give it?  Could you point me to a site that will show me how to increase the .vmdk file if I run out of space in the future?

Thanks for putting up with me Rebelli0us :P

I think you're sweating the details too much. :popcorn:

Win7 will run in VM even with 1/2 GB ram, assigning more cores makes no real difference. I have 20GB virtual disk, you can clone it or increase it later as needed.

---

