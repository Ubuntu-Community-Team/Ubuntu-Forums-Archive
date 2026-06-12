---
title: "cloning ubuntu from one partition to another"
date: 2010-08-10
forum: General Help
---

### Post by ibrabeicker on 2010-08-10
I had to change my disc for a bigger one, and i want to transfer all my data, configurations, etc to a partition in another disk, a simple ctrl C, ctrl V will do or theres a specific tool that i need? I dont want to download all the updates, programs and go through the hassle of reconfiguring everyhting

my new disk have windows 7 and i installed a fresh ubuntu on it but i want it to be a clone of my old one

PS: i just notice now that grub no longer recognize both win7, the old and the new. What's wrong?

---

### Post by Ozymandias_117 on 2010-08-10
You will need to copy everything from your old partition to your new partition. I would advise booting to a liveCD to make it easier. Make sure the new partition is formatted to the same as the old, then you will need to rewrite your MBR. [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows")

---

### Post by dcollier on 2010-08-11
Try cloning the hard drive with ping.  After restoring the clone to the new partition you can you gparted to resize the partion. "bc it will restore to the original size of the clone"

---

### Post by ibrabeicker on 2010-08-12
solved, Gparted from ubuntu live cd works great

---

