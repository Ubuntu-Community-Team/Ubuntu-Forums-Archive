---
title: "Ubuntu MID/XBMC Live - formatted the wrong partition"
date: 2011-04-01
forum: General Help
---

### Post by Lic on 2011-04-01
Hi!

Figured to post this here because XBMC Live is based on Ubuntu.

So, when installing XBMC Live, I managed to install to the wrong partition. It's a 2TB 5400rpm Samsung drive with one partition on 100 GiB and another on 1.9 TiB. Anyway, now the 1.9 TiB partition is formated! I haven't touched it since the install, so the OS is the only data written to it. I Booted up in Geparted to confirm that the 1.9 TiB partition was the one which was formated, and it is:(

It was about 700gb of stuff on it, so it's kind of a crisis.
Is everything gone forever, or is it still hope?

Thank you very much for all answers!

- Lic

---

### Post by coldraven on 2011-04-01
This sounds bad!
Firstly don't use your machine, you have already lost about 2GB that's been overwritten, you don't want that to increase.
If your data is valuable the you should think of cloning the drive to another, use Clonezilla maybe then trying to recover data from the cloned drive
Obviously you'll need to buy another 1TB drive.
Try downloading Parted Magic from here: [http://partedmagic.com](http://partedmagic.com) and burn it to a CD.
Don't do this on your machine, use another.
Boot up with Parted magic then use the utility "Testdisk" on the cloned drive, it might be able to recover the partition.
Read the instructions here: [http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)
Good luck!

---

### Post by Lic on 2011-04-01
Hi, coldraven!

I booted with a Mint Live CD and checked out the situation closer. Turns out the OS isn't installed on that partition. However, everything on it except the lost+found dir (which is 27gb) is gone.

Anyway, why do I have do use another machine? I would of course move the drive from the HTPC to my desktop (with Windows on it) if I have to, but why can it not be done on the HTPC?:)

Thanks again!

---

### Post by coldraven on 2011-04-01
I'm sorry if I did not quite understand.
I thought that if you boot up the HTPC it would be writing even more stuff to the disk with your data on it.

---

### Post by Lic on 2011-04-01
No need to apologize:P
I thought so too. When I booted Gparted I just saw the partition was almost empty, and therefore assumed the used space was the new OS. When closer inspection I discovered the only thing which is on it is the lost+found dir at 27gb. However, it is the same size as it was before the install of XBMC Live, because I remember noticing the size of it was remarkably huge. Therefore it looks like that folder was never deleted, unless 27gb is a standard size of a lost+found dir.

Bottomline. Except for the lost+found dir, the 1.9tib appears to be empty. After reading some threads about pulling deleted data from ext3 and ext4 partitions, I don't have a clue about half of what they are saying. Plus the fact that most say recovering data from an ext3 or ext4 partition is a bitch, it doesn't look bright, does it?

However, it must be a very usual rookie mistake, right? BTW, for the record, it's the drive in my HTPC I'm refering to:)

Anyway, thanks again!
- Lic

---

### Post by LostFarmer on 2011-04-01
check out the last 2 posts.
[http://ubuntuforums.org/showthread.php?t=1552484](http://ubuntuforums.org/showthread.php?t=1552484)

---

