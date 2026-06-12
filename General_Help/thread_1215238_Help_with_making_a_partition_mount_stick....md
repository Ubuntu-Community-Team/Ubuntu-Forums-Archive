---
title: "Help with making a partition mount stick..."
date: 2009-07-16
forum: General Help
---

### Post by TheSmokingGNU on 2009-07-16
Well, I'm running 8.04, and I finally figured out how to make my windows partition read and writeable in Ubuntu. Problem is, I have to type

sudo mount /dev/sda1 /media/c

each time I restart my system.

Any way to make this a permanent fixture?

It's not terribly important, but it would save me some crazy points.

Thanks in advance!!

---

### Post by merlinus on 2009-07-16
```
sudo apt-get install ntfs-config
```

Restart, and then look in Applications/System Tools.

Tick the appropriate boxes and put in the mountpoint, restart, and you should be good to go.

If not, post back and we can set it up with an entry in /etc/fstab.

---

### Post by TheSmokingGNU on 2009-07-16
Oh, man! You rock! Thanks so much.

Merlinus is my new favorite person.

---

### Post by TheSmokingGNU on 2009-07-16
oh hey, one more question: is there a way to upgrade to the latest distro without losing my files?

---

### Post by merlinus on 2009-07-16
If you hae a separate /home partition, where is where your data, application setups and configurations, email, and bookmarks live, then no.  You choose to use it as ext3 with a mountpoint of /home during partitioning, but NOT to format it.

If /home is part of the / partition, then you will have to back up everything, including the contents of the hidden directories, or lose it all.

However, you can set up a separate /home partition, if you do not currently have one, before installing a new version.

Info here:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

If you do an upgrade rather than a fresh install, then none of this will be lost, even without a separate /home, but there have been a fair number of difficulties with this approach detailed on the forums.

---

### Post by zeronothing on 2009-07-16
Before you upgrade to the latest distribution, backup your files first. then all you have to do is open up terminal and execute this command:

sudo update-manager -d

This will allow you upgrade to the latest version of ubuntu.

---

