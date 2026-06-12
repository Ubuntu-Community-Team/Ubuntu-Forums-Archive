---
title: "Btrfs and fsck again."
date: 2012-01-04
forum: General Help
---

### Post by kajman on 2012-01-04
Hi all,

first of all I'd like to apologize for asking about this issue again (it seems this topic is talked about over and over), but I cannot get definitive answer.

Is there or not fsck tool for btrfs?

According to btrfs wiki:
> Note that Btrfs does not yet have a fsck tool that can fix errors.
But the wiki seems outdated, no new info for about an half a year.

But, on the other hand, I've installed Ubuntu 11.10 as an VM to test it. I created btrfs partitions for /root and /home and started system upgrade. During the upgrade I've killed the VM with 9 signal to "simulate power failure". After reboot the filesystem was checked (and repaired?) and system booted up normally.

Also according to [[COLOR="Red"]_this wiki page_[/COLOR]]("https://help.ubuntu.com/community/btrfs") you can fsck a device issuing for eg. ```
sudo fsck /dev/sda1
```.

Is this a program from package btrfs-tools and it is installed automatically with newest Ubuntu?

Lastly, with existing tools, is it safe to use this filesytem for everyday purposes (not at work, just home desktop)? Anyone has some experience with such failures already?

cheers,
kajman

---

### Post by The Cog on 2012-01-04
fsck.btrfs is in the btrfs tools package, but as far as I can tell from scouring the web, it only lists problems it finds - it cannot fix them. Lots of people are waiting for a btrfs fsck that can actually fix problems.

---

### Post by kajman on 2012-01-04
I'm also waiting impatiently. Do you know where can I follow development updates regarding this issue (and btrfs in general)?

I've read some mailing lists but it is very inconvenient, as it is hard to find any important news.

Honestly I can't wait until I can finally move to this filesystem, as I find it extremely appealing :D

---

### Post by The Cog on 2012-01-05
No. I occasionally google for "btrfs fsck" with a time limit of the last month, that's all. 

I am using btrfs in a couple of places, and using snapshots. The only time I have seen problems is when unplugging a USB btrfs drive - even after umount and sync, this can cause a kernel crash. It seems OK if you give it 5 minutes after umount though, so maybe the sync isn't doing its job properly.

---

### Post by kajman on 2012-01-05
Using snapshots seems like an great idea! Didn't think of it myself! Thanks! I think I can move to btrfs now :)

But snapshots are kept within btrfs so aren't they at risk also?
How often do you make your snapshots? I was thinking about making hourly - daily - weekly - monthly snapshots (something like rrd records) keeping up to 24/7/4/1 in each category. Do you think it is possible and fast enough? This way any file I delete is kept in history for a month along with any modifications on the way.

If I understand correctly, those would take negligible amount of space as long as I don't remove/modify a lot files? (since only differences are kept on those).

What about torrent usage in above scheme, and btrfs in general? Isn't a COW fs a very bad choice for using torrents?

cheers,
kajman

---

### Post by rossmoore on 2012-01-05
So yes, there is a BTRFS fsck tool. The problem is that, as it says on the wiki, it only detects problems and can't fix them.

Supposedly Chris Mason, the Oracle employee who leads the develpment of BTRFS, has been working to finish of the fsck tool that can fix problems since late November (following the 3.2 kernel code release). As usual, there's little in the way of information updates comin from him, and like TheCog I continue to check every month or so to see if there's any update.

I use BTRFS on my home media server for its RAID-like abilities and have had no problems so far (in about 9 months). I have a RAID1-like array of 2*2TB and 1*1TB hard drives, and have successfully added a hard drive to expand it with no issues (although the rebalance took all night to complete). I continue to be slightly nervous that I could lose the lot sometime though until this fsck tool is released...

The linux-btrfs kernel mail-list is the place to subscribe to - my link goes to a recent discussion about timelines:
[http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg14174.html](http://www.mail-archive.com/linux-btrfs@vger.kernel.org/msg14174.html)

---

### Post by kajman on 2012-01-05
@rossmoore Thanks for the link. Have you experienced any power failures during that time? I run my system on a laptop which is using all CPU to compute some boinc stuff so it overheats occasionally or runs out of power within minutes if I unplug power adapter accidentally. It happened to me many times before, but ext4 recovers nicely in such scenario (at least up to this point).

---

### Post by rossmoore on 2012-01-05
@kajman Yes I have - although only of the "hold the power button for 5 seconds" type. However, I only use BTRFS on the media mount, not on the root filesystem itself. Any corruption on a power failure might only occur if you're writing to the filesystem at that point (and it fails at just the wrong moment), and I only write to that mount point in short, infrequent,user-controlled burts - copying a file off DVD, writing a document, etc.

---

### Post by kajman on 2012-01-05
Well, I must say, that after the discussion above I'm very convinced to give it a shot. I'll leave root fs with ext4 for now but I'll convert home to btrfs and start making snapshots in scheme detailed above.

Thank you both for some decent advice/experiences.

cheers!

---

### Post by kajman on 2012-01-05
After thinking a bit more I have new doubts about snapshots.

If I understand it correctly snapshot is a set of pointers to data with some checksums and if a piece of data on fs is changed then the old data is copied and pointer is updated (or is it the other way? new data is written in new place, and fs pointer is updated, but snapshot is left intact?) 
So what if I'm writing data on disk being snapshotted and I get a power failure? Will the newly, corrupted data affect the snapshoted copy? 

After writing the above I think there is no risk to loose data :P but I'd appreciate your opinion in that matter.

---

### Post by The Cog on 2012-01-06
That's pretty-much as I understand it. I believe that the new data is written before the metadata (pointers etc) are updated. Since the old data is left untouched, you should not see any corrupt data ever. And if the old data is still referenced by a snapshot then it is not eligible for deletion. It all sounds good as far as I can understand it, which isn't all that much - just reading other journalists articles.

I have run my home desktop on btrfs for a while now. At one point I had three subvolumes sharing the same partition, being used as /home, and two different / mounts for two different Ubuntu versions. I thought it was a little slow, so backed out of that arrangement a few months ago. It seems that the filesystem wasn't the reason for the slowness though, so come 12.04 I think it's all going back on a single btrfs with subvolumes. 

My lappy has a btrfs /home which I snapshot every few weeks. I don't snapshot it very often because of the huge VirtualBox virtual disks - I don't want to use up all the space with old snapshots of those. I really ought to move them out to a separate subvolume so they don't get included in the normal snapshot. I also take backups fairly often, just in case.

---

