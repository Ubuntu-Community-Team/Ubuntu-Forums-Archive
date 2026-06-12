---
title: "Help installing an expandable raid5 server"
date: 2006-06-13
forum: General Help
---

### Post by bigmell on 2006-06-13
Got dapper running on three boxes and it is running great.  With automatix and all the guides on the web getting a new system up and running is a breeze.  I have one request.  I've googled around and cant find a good answer for this.

I would like to make one of my machines a file server.  I have an assortment of disks that I would like to put all together into a software raid.  I dont want to be locked in to a raid that only certain types of raid cards can identify.  Been down that road once, it sucks.

I have 2 200 gigs (one sata one ide), 2 300 gigs (ide) and 2 50 gigs (ide) and I would like to combine these into one raid5 array.  This is not the problem itself, but I would like a software raid5 tool that had the ability to do 2 extra things.

First I would like a tool that can recognize newly added disks, and grow the raid5 array at will, automagically correcting parity etc without having to move data around and create a new array.  Is this sort of thing possible?  And if so what tools do I use to pull it off?

And the other thing, if possible of course, I would like to be able to create this raid5 array without erasing data on the disks.  There is already data on one of the 200 gigs, and one of the 300 gigs, they are both about 90% full and I dont really have anywhere to store all that data while I create this raid5 array.  Which will be where all the data will eventually end up anyway.

Something with these requirements would be optiimal for me.  I can just grow it bigger and bigger in the future making it a pretty good "forever" file server with parity in case the drives fail (those 50 gigs are kind of old).

So anyway thanks for your help.  Hopefully there is some easy solution that I just missed  :)

---

### Post by zitch on 2006-06-13
I have never heard of such an animal, either software based or hardware based.  Several points:

1) A RAID 5 will have to occupy the same size "stripe" on each disk.  So in your setup, you might be able to create a 6-disk RAID 5 using 50 gigs of each disk, then a 4-disk RAID 5 from 150 gigs of the 200 and 300 gig disks, then a RAID 1 with the last 100 gigs on each of the 300 gig disks.  Remember, your standard RAID 5 configuration in hardware require that each of the disks be the same size (or will be limited by the size of the smallest disk), you might be able to get around that in a software RAID.

2) I've never seen anything that will allow you to simply add a disk to an already running RAID 5.  Even theoretically, this will involve a massive reorganization of the data and parity stripes in addition to the recalculation of parity.  This is not a trivial task.

3) My recommendation is to setup all of the like-sized drives as RAID 1 arrays and use [LVM](http://www.tldp.org/HOWTO/LVM-HOWTO/) to have the ability to move and resize partitions on the fly.  I've never used LVM myself (yet), but it looks like you'll be able to increase capacity by simply adding new drives (I'd recommend getting new drives in pairs this way and setting them up as RAID 1) and expanding the existing partitions onto these drives.  You'll have to get more specifics and ideas of this from elsewhere, though.  I've only been reading about it and haven't had a chance to really play with it.

4) Another reason I recommended a RAID 1 is because it's more likely tools will exist that will be able to mirror the data you have without having to initialize it first.  All this basically consist of is a straight copy of data from the full disk to its pair in the mirror.  As for actually creating the RAID 1 and having LVM running without destroying the existing data, that I don't know of tools that can do this.

ADD:  Ok, so I'll have to extract my foot out of my mouth a bit.  I just did a search on google on "Creating RAID 5 from existing disk" and saw that there *are* hardware controllers that have the capability to add to a RAID 5.  Nothing on software RAID 5 or on creating a RAID 5 from a disk with data while including that disk as part of the array.  And as far as I can see, those were all SCSI RAID controllers; nothing on PATA or SATA.

---

### Post by MikeNick42 on 2006-06-13
I have been interested in the same thing for a while.  This is the closest I've been able to find:
[http://www.infrant.com/](http://www.infrant.com/)
Their RAID-X is exactly what you describe.
It is limited to 4 drives though.

---

### Post by bigmell on 2006-06-15
Thanks for the help guys.  What I've found so far seems to basically be to forget creating a raid array on disks that already have data.  There are some commercial solutions that support this but md doesnt support anything like this so...  Bah...  But I have a partial workable solution.

I am going to buy a few extra drives so I have 3 250 gig, and 3 300 gig drives

I am going to 
1. store data on the 300 gig drives that already is on the 250 gig drives.  
2. create a software raid on the 250 gigers.  
3. use LVM on the 250 gig raid 5 array.  
4. copy the data from the 300 gigs back on to the 250 gig raid array
5. create a new raid 5 array from the newly empty 300 gig 
6. use lvm to add this new space to the other 250 gig drives.

It is a pretty good solution in that if I ever want to add more drives via a pci sata card or something, I can create a new individual raid 5 (or whatever) array, and add it to the big lvm drive.  Since all the raid arrays are raid 5, if it fails, I can replace the bad disk in whichever array failed, and lvm should continue to work fine.  I lose a bit more storage this way (one disk per raid 5 array gone to parity) but I have a big (1+ terabyte) expandable fault tolerant nas solution.  The only thing I am concerned about slightly with this setup is speed with the lvm running on top of a software raid.  I am only slightly concerned though because this will all be running on a headless 3ghz box with a gig of ram.

Hopefully this helps someone out trying to create an expandable nas like me!

And p.s., I would like to go with 4 250's and 4 300's, but my motherboard has 4 sata and 4 ide ports and I need one sata for the drive linux will actually be installed on, and one ide for the dvd burner.  MUST have a locally attached dvd burner  :)

---

