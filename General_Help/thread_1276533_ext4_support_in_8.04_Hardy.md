---
title: "ext4 support in 8.04 Hardy"
date: 2009-09-27
forum: General Help
---

### Post by louieb on 2009-09-27
On a hoot  I formatted a partition with the ext4 filesystem. When I try to mount it I get this: 

```

/home/lou%>cd /mnt
/mnt%>ls
ext4fs
/mnt%>sudo mount -t ext4 /dev/sda6 ext4fs
[sudo] password for lou: 
mount: unknown filesystem type 'ext4'

```and when I try to browse it using nautilus I get this:[IMG]http://louboldt.com/p_mnt_ext4_hardy.png[/IMG]

Did a search in Synaptic for ext4 - did not get a  hit.
Any ideas?

---

### Post by jerrrys on 2009-09-27
think we have to wait for the next LTS for ext4 support...

---

### Post by TuxIsCute on 2009-09-27
Jaunty has full ext4 support.  In fact, I installed Jaunty onto an ext4 partition.

:KS:popcorn::KS

---

### Post by louieb on 2009-09-27
> **jerrrys said:**
> think we have to wait for the next LTS for ext4 support...
Did some Google.  Found a hit on [kernel.org]("http://ext4.wiki.kernel.org/index.php/Ext4_Howto#For_people_who_are_running_Ubuntu") about ext4 in Hardy. Does not look like anything I want to do without a backup... Maybe I'll try it later.  
>  Packages for Ubuntu Hardy are available [here]("ftp://ftp.kernel.org/pub/linux/kernel/people/tytso/ubuntu-fixed-util-linux").   These packages revert a [change made by Ubuntu]("http://changelogs.ubuntu.com/changelogs/pool/main/u/util-linux/util-linux_2.12r-19ubuntu1/changelog") to use the volid library instead of the blkid library. The volid library has a number of shortcomings, including that they don't work on freshly created filesystems or swap devices until after you reboot (since it is tied to udev probing) and the volid library doesn't understand ext4dev filesystems.

---

### Post by edouardp on 2009-09-27
> **TuxIsCute said:**
> Jaunty has full ext4 support.  In fact, I installed Jaunty onto an ext4 partition.

:KS:popcorn::KS

Correct me if I'm wrong, but using ext4 with the 2.6.28 kernel shipped with jaunty is a bit risky. There were bugs which could cause data loss in special conditions.

louieb, the only way to get ext4 to work in hardy is to recompile a recent kernel yourself, and yes, you want to make a backup before :p

---

### Post by louieb on 2009-09-27
Thanks to all for your input. 

Went ahead did my backup and downloaded the 5 packages from kennel.org. The installer said I already had newer versions of 4 of the packages.   

Plus Hardy uses the 2.6.24 kernel. And for ext4 support I would need the 2.6.28 or later kernel. 

Just not that bored or ambitious  - Think I'll wait till next year when 10.4 comes out.

---

