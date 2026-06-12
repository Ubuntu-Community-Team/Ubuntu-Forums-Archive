---
title: "Can't access old partition with Lucid after installing 12.04"
date: 2012-08-07
forum: General Help
---

### Post by andrewcd on 2012-08-07
Hi All,  reviews of cinnamon finally convinced me to make the jump from the sinking ship that is gnome 2.  I went and installed linux mint 13/cinnamon, but after 15 minutes of trying to figure out how to turn the icons orange, I decided that it'd make sense to just install ubuntu 12.04 and cinnamon along with it.  

I must have screwed something up when I deleted the linux mint partition and installed 12.04 on top of it, because now I can't boot into Lucid, nor can I access the files.  I've attached a screenshot of the disk utility.  How can I (or can I?) re-establish dual-boot?  And how can I get to my old home directory from 12.04?  The two partitions (the 45GB one and the 39 GB one) were both put thereby the linux mint installer when I set up the mint dual-boot.  One of them has lucid, and one of them has my home folder (I think).

I want to ease my way into cinnamon, and preserve an avenue of retreat for myself, in case I find myself hating cinnamon as intensely (or even half as intensely) as I hated gnome 3 and unity.

Help much appreciated.

---

### Post by efflandt on 2012-08-07
From what you show, you only have 1 ext4 partition on that drive, so somewhere along the line installing Mint14 or 12.04, you no longer have a Lucid partition.  I always manually partition before (gparted) or during install, so I know what is happening.

Not sure if **testdisk** could recover any Lucid files after partitioning and installing other operating system(s) over it.

---

### Post by andrewcd on 2012-08-07
I'm pretty sure that lucid is installed on one of those two.  Anyway, when I was dual-booting between mint and lucid, the lucid partition was sized on the order of those two partitions in the screenshot.

---

### Post by andrewcd on 2012-08-07
and I've done a full backup, so no worries about data -- I'd like to be able to boot into Lucid to get actual work done however, rather than waiting weeks (if ever) until I am fully functional in 12.04.

---

### Post by dcstar on 2012-08-08
> **andrewcd said:**
> I'm pretty sure that lucid is installed on one of those two.  Anyway, when I was dual-booting between mint and lucid, the lucid partition was sized on the order of those two partitions in the screenshot.

There is only **one** Linux partition, if you are booting 12.04 then that is the only partition on your system and **you have deleted** all other Linux partitions.

---

### Post by andrewcd on 2012-08-08
> **dcstar said:**
> There is only **one** Linux partition, if you are booting 12.04 then that is the only partition on your system and **you have deleted** all other Linux partitions.

well, you'd not use bold if you weren't sure of yourself.  

out of curiosity, why would a mint live cd make those two partitions if linux only lives on one partition?  and what could be in those two unaccessible partitions (there is no windows on my machine)

---

### Post by Cheesemill on 2012-08-08
You only have 3 usable partitions on your drive:

115GB ext4 partition
39GB NTFS partition
5.7GB swap partition

The 45GB partition is actually an *extended* partition which means that is just a container for your NTFS and swap partitions, it isn't used for actually storing data on (apart from the partitions it contains).

---

### Post by andrewcd on 2012-08-08
OK, well, if the linux gods are listening, they should take note of my case as an example of how they really should simplify their partitioning software, and better communicate what the hell is going on.  I'm no programmer, I just want two operating systems that I can switch between when I log on.  Like "ext4" means anything to regular people who use computers?

Since I don't have anything on those partitions anymore, how can I fold their space into my current partition with 12.04, without nuking my OS yet again?

---

### Post by andrewcd on 2012-08-08
and what is on that NTFS partition anyway, and why would a Mint live CD make it for me?

---

