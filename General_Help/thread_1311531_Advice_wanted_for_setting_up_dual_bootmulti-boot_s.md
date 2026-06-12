---
title: "Advice wanted for setting up dual boot/multi-boot system"
date: 2009-11-02
forum: General Help
---

### Post by Brian Vaughan on 2009-11-02
I've got a new 500 GB hard drive coming, and I want to plan a dual boot or multi-boot system.

I've been happily using Ubuntu for quite some time, and I removed Windows from my system entirely, which proved to be precipitous -- for purposes of professional training, I'll need to keep up with Microsoft, even if my specialty is FOSS software and operating systems.

I may have panicked a bit at Palimpsest's report of bad sectors on my old hard drive -- I hadn't had any real trouble -- but I was thinking of getting a new one anyway.

The simple and obvious thing to do would be to install Windows 7 first in a 100 GB partition, then have a 2 GB swap partition, about 30 GB for the Linux root partition, and the remainder for the /home partition. It will be a fresh install of Linux, and root and /home will probably be formatted ext3. I'll keep my old 250 GB hard drive around -- I'll copy over the documents, music files, and so forth to the new accounts, then keep the old drive as-is for a few months just in case I find I've missed something. Later, assuming the old drive is stable, I'll wipe it and set it up as a backup for /home on the new drive.

Would it work well to use gparted to partition the new hard drive before I installed Windows and Ubuntu on it?

There are some other options I'm considering: having a separate partition, probably NTFS, for music files, so both OSes can access it; and, leaving unallocated space for other, alternate OSes. That might make for some complications: in particular, the limitation on the number of primary partitions.

So, I'm looking for comments and advice.

---

### Post by ajgreeny on 2009-11-02
Put your windows in the first primary partition of whatever size you want, and then you can make an extended partition of the remainder and put all your other partitions into that.  Linux distros will boot without problem from extended partitions, so don't worry about that.

30GB for root is much larger than most people would use, 10GB is more normal, but you could always make a number of 10GB partitions and leave some of them empty until you want to put another distro on to them.

Gparted should work OK, I think, to make the partitions, but may not be able to format to ntfs when running from the live CD; not sure about that though so you can try.  As long as you then point to the right partition when installing windows it should go OK, as far as I can see.

---

### Post by Tahakki on 2009-11-02
You could think about having a SSD to store OSes, and then your big drive for files etc?

---

### Post by ranch hand on 2009-11-02
I think the 30Gb / is about right on that large a drive.  I like to keep my partitions below 50% full.  they are faster that way.  If you are programing you are going to have all the src stuff on there too, maybe more than 1 kernel.  It adds up.

I would put Win JerryLewis pro on the primary and make the rest extended.  I would put the swap at the end.  I would also use ext4.  That way you can get into MS files but MS can't get into yours.  Seems more secure to me, but I do not have to have that malware on my box, you poor guy.

---

### Post by Brian Vaughan on 2009-11-02
Well, most likely I would only want two OSes, really: Windows, and Ubuntu Linux. I've been using VirtualBox to host a few other distributions, which is probably adequate, since I just want to be able to experiment with them a little -- I don't really need the full power of my computer to try out the package manager in Fedora, for instance.

My thinking was just that if I'm getting an absurdly large new hard drive anyway, I may as well consider to what uses I could put the extra space.

I'm leaning towards ext3 rather than ext4, since I'm getting the impression that ext4 doesn't really have all the kinks worked out yet, and I'm not all that worried about file access time. (In fact, I decided to go with a "green" hard drive that uses less power, at the tradeoff of lower RPMs.)

---

### Post by ranch hand on 2009-11-02
I have been using ext4 since before 9.04 was released and have been hearing these stories about it too.  I do not believe them in the least.

There are 2 main reasons to go to ext4.  Support for large files and large HDDs.  If I were you I would go with it and ignore the buggers that want to blame every problem they have on ext4 instead of where is really belongs.

That size drive would be nice for VB.  You could run a bunch of stuff.

---

### Post by Brian Vaughan on 2009-11-02
On ext3 versus ext4: I've been reading Theodore Ts'o's [blog discussion on the problems with ext4]("http://thunk.org/tytso/blog/2009/03/12/delayed-allocation-and-the-zero-length-file-problem/").

As far as I understand it, Ts'o is arguing that the problems with ext4 are really exposing that many applications have been written sloppily -- failing to use fsync() -- and if they'd been written properly and conformed to published standards, there'd be no problem. Perhaps, but until all those applications are rewritten, I'll stick with the more stable, if slightly slower, ext3.

---

### Post by ranch hand on 2009-11-02
Note that the blog was written in March.

I am sorry but that is a long time ago in terms of all this.

You could not your "small" drive install, using the format that is native to it, a 30Gb single partition install of 9.04 or 9.10 and try it your self.

I think that would convince you that the sky is not falling and ext4 is not dangerous to use.

---

### Post by Brian Vaughan on 2009-11-13
A different approach: could I copy the partitions from my old hard drive to the new one, perhaps within an LVM, and then use the old drive for Windows OSes?

I'd expect I'd have to tweak my fstab, at least, for this to work. I'd want to make sure partitions were labelled, and mounted by label instead of by UUID.

But would this work reasonably well, otherwise?

Presumably I'd have to recreate the MBR using GRUB.

Edit: Correction, UUIDs are fine, and actually help me here. It's mounting by device I want to avoid. I'm still not sure if I could use LVM, though.

---

