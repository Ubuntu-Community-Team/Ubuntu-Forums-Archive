---
title: "BTRFS questions"
date: 2011-08-24
forum: General Help
---

### Post by blur xc on 2011-08-24
First, I should explain a bit what my use case and requirements are.

I'm an amateur photographer, and shoot tons of pictures.  It's really not hard to rack up 5gig of photos in one day shooting an event or whatever.  Right now my 1tb drive is filling up pretty quickly, and with every new generation of camera, the file sizes keep getting bigger and bigger.  My old camera shot 3mb jpegs, the current one, ~12mb compress raw files, and the new one just announced today is rumored to take up to ~24mb per photo.

Also, as of now, I'm playing a very dangerous game, since I do not currently have any backup system.  Lots and lots of data causes quite the problem since it's not so easy to move it around from place to place.

Originally I had settled on trying to build a software raid setup.  I ruled out a hardware raid due to cost, and insecurity in knowing that in the expensive controller card took a dump my data would be gone (correct me if I'm wrong).  A fake raid (mobo raid) for the same reason, the filesystem would be tied to the mobo.  As I understand it, the Ubuntu software raid isn't that hard to move from one computer to another and is just more flexible.  But, with a raid (I'd be interested in a raid 5) I also understand you need to have identical sized partitions.  So, say in 5 yrs from now if I want to grow my raid built out of 2tb drives, and there are commonly available larger drives on the market, it'd be stuck shopping for more 2tb drives.

Then I heard bout zfs, and it's linux cousin, btrfs.  As I understand it, you can build a file system out of all kind of mis matched partitions, and grow them however you want.  If 5 yrs from now I need to add space, I could plop on a 5tb drive (pretending in 5yrs that's a commonly available size) and remove an aging 1tb drive, etc., etc.,.   I also understand it has all the same backup redundancy benefits of a raid array...

So, if I were to string together a few drives to build a btrfs array, what's the easiest way to do it?  A complete and total idiots guide written for the layman would be great.  So much information assumes you have a fair amount of base knowledge, so if you don't, like me, you are lost after the 2nd paragraph.  I google around and 90% of what I find is all about setting up a btrfs file system as your boot partition but I have no need to boot from it.  I'm more than happy to boot off of another smaller drive and just use the btrfs for mass file storage.  That, or how to compile tons of stuff from source code.  I'd much rather not have to do that.  Is there any way to practice off line in a virtual machine or is that too complicated?  What are the risks, if any, involved with managing a large btrfs setup?

Thanks,
BM

---

### Post by The Cog on 2011-08-24
[https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices](https://btrfs.wiki.kernel.org/index.php/Using_Btrfs_with_Multiple_Devices)

But personally I would recommend using an entirely separate disk(s) for backup. One software or typing error can erase a file system contents. If you're relying on raid of any kind, that error will be faithfully replicated across all your backup drives. And BTRFS doesn't have an fsck disk repair utility yet.

I don't have the same number of pictures as you do, but my wife did take several thousand photos on our last holiday and would have done more if she hadn't dropped the camera onto tiles early on. I use an external hard drive and use the program **rsync** to update the backup drive (much quicker than a full copy) occasionally. Then the external drive goes back in the cupboard.

---

### Post by blur xc on 2011-08-25
thanks for taking time to reply...

I'm still on the fence a bit on weather or not to use an hdd array or do  like you do and just do daily backups to another drive.  It would  really help with my workflow to always have all my files on one  filesystem, whether it's an array or a single drive.  *** long as HDD  sizes (or whatever storage devices are in our future) grow faster than  my data volume, the nightly backup deal should work out fine.  Right now  newegg has 3tb Hitachi drives on sale for $110 ea.  Two of those  puppies would hold me over for a couple of years...

I did go ahead and create a btrfs array in my Ubuntu VM.  I just created  a couple of blank .vdi files and mounted them up in my VM.  It seemed  pretty simple and straightforward, with the exception of the "WARNING  EXPERIMENTAL" messages...

I assume that with a BRFS array, with the data striped across all  devices, if one failed, it'd be as simple are replacing the failed drive  and the data would be restored, correct?  I read a lot bout metadata in  the btrfs wiki but I don't think I really understand what filesystem  metadata is.  

Thanks again,
BM

---

