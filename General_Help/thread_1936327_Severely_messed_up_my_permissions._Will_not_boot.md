---
title: "Severely messed up my permissions. Will not boot"
date: 2012-03-05
forum: General Help
---

### Post by cisasteelersfan on 2012-03-05
Some background- I wanted to install crunch bang on a laptop. I used sudo dd to copy the files to a flash drive. Later, I plugged the flash drive back in this computer and it said 'read only filesystem'. So I Googled a bit and someone mentioned fsck. Well I typed that in and pressed y a few times. Then I did a sudo apt-get update but it had an error. 


When I restarted the computer, I had this message: "can't execute '/sbin/init' permission denied"
I've desperately been Googling ever since but nothing has worked. I booted from a flash drive and mounted the drive and looked at the fstab but that looks fine to me. I think it has something to do with either permissions or a read-only file system.


I know I made a VERY stupid mistake for running fsck to my mounted, root directory. Can anyone help me?? Thanks

---

### Post by iponeverything on 2012-03-05
found this googling "can't execute '/sbin/init' permission denied"

[http://www.tek-tips.com/viewthread.cfm?qid=1456710](http://www.tek-tips.com/viewthread.cfm?qid=1456710)

sift through some of the search results for other possible solutions.

---

### Post by iiiears on 2012-03-05
the permissions are set root read and write and group root read-only on files and links in /etc/init.d

---

