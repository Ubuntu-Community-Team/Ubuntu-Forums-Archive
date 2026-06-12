---
title: "Problems writing to ext3 partition from Vista"
date: 2010-04-29
forum: General Help
---

### Post by mpsaris01 on 2010-04-29
Hi Guys,

I've been using Ubuntu 9.10 for a few months now.  Just recently I reformatted my hd and reinstalled Vista and Ubuntu with a shared data partition.  The shared partition is /home for Ubuntu and so I formatted it with ext3 with the expectation that I'd use fs-driver to read/write from Vista.  It's working....sort of.

Problem 1)  Bittorrent in Vista caught an error when I was trying to download a file larger than 5gigs to the shared partition.  I restarted it multiple times, but to no avail.  I then changed the destination folder to one in the NTFS partition.  All 5 gigs downloaded without a problem this time.  

Problem 2)  Once this file finished downloading, I tried to copy it over to the shared partition.  All the files copied except for one lonely song.  The error that came up is "Could not find this item...This is no longer located in C:/Users/.... Verify the item's location and try again."  I've copied this file to other locations on the NTFS partition, and it works fine.  I then tried copying to different locations on the ext3 partition, and the same error comes up every time.  Anybody know what's going on here?

---

### Post by twright on 2010-04-29
It really is not a good idea to continue using that driver as it is designed for older filesystems - if you need to share files then an ntfs partition is probably the easiest way to do that.

---

### Post by arrrghhh on 2010-04-29
Having Windows machines write to ext2,3 or 4 partitions is a BAD idea.  Read-only is doable, but again not recommended.

An NTFS partition that neither depend on OS-wise is the way to go.

---

### Post by mpsaris01 on 2010-04-29
> **twright said:**
> It really is not a good idea to continue using that driver as it is designed for older filesystems - if you need to share files then an ntfs partition is probably the easiest way to do that.

So, how would you suggest I set up my /home partition since I can't format it in NTFS?

---

### Post by egalvan on 2010-04-29
Despite what the nay-sayers are touting, here is an up-to-date driver that can be trusted to work with ext3


[http://www.ext2fsd.com/](http://www.ext2fsd.com/)


sadly, fs-driver has fallen behind in support.
it does not support large i-nodes, which all modern Linux kernels use by default.
Perhaps if more users had donated a few bucks...

---

### Post by arrrghhh on 2010-04-29
> **egalvan said:**
> Despite what the nay-sayers are touting, here is an up-to-date driver that can be trusted to work with ext3

Just seems like a bad idea to me, I wouldn't want any Windows systems touching my Linux partition, I've seen what it does to its own file systems!!!

> So, how would you suggest I set up my /home partition since I can't format it in NTFS?

Don't use your /home to share with Windows, create a new NTFS partition that neither OS depends on like I said previously.

---

### Post by VinisLentoje on 2010-04-29
You could probably do it the same what I do:
Do not use the /home partion as the "main" filesystem (or as I would say, do not use it as the "main file-dumpster"). Use some other partition instead, most logically. For example, something located in /media/ maybe?
To note, my /home/ partition is only ~2% of my total disk space (~19 GB)

"keep my stuff in some lame /home partition? meh.." ~I thought

---

### Post by twright on 2010-04-29
Note that if you want files to appear as-if on either partition when they are shared, you can use links. You could also mount the shared directory as a subfolder of your home if this makes things easier.

---

### Post by mpsaris01 on 2010-04-30
Alright, after reading the responses and doing a bit more research, it seems like the best plan is to move /home onto the Ubuntu partition since there's no reason for it to have it's own if I'm storing files elsewhere, and then reformat my shared partition in ntfs, and link to that from the new /home(per twright).  

egalvan, unfortunately I'm already using the version you suggested.  Before I repartitioned and reinstalled everything, reading/writing to an ntfs partition from ubuntu seemed to work fine, so I'm inclined to go that route unless there is some other easy correction to the driver that you know of.  Plus I'd rather not deal with software that is unsupported ;)

Thanks for the help guys.

---

### Post by dino99 on 2010-04-30
my 2 cents:

as many users i was a windows guy before using ubuntu, and i've dual boot several years long before completely removing windows.

Now ubuntu + wine is the solution for my oldish or not so old windows designed apps, and its fine.

---

### Post by mpsaris01 on 2010-04-30
> **dino99 said:**
> my 2 cents:

as many users i was a windows guy before using ubuntu, and i've dual boot several years long before completely removing windows.

Now ubuntu + wine is the solution for my oldish or not so old windows designed apps, and its fine.

Agreed.  Wine is great for some things.  I've already found applications that don't work with Wine though, eg Garmin GPS  software.

---

### Post by dino99 on 2010-04-30
> **mpsaris01 said:**
> Agreed.  Wine is great for some things.  I've already found applications that don't work with Wine though, eg Garmin GPS  software.

forget to talk about winetricks, often needed too

---

