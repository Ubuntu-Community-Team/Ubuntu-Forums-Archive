---
title: "rsync: failed to set times on &quot;/media/NAS&quot;:"
date: 2011-05-16
forum: General Help
---

### Post by fisheater on 2011-05-16
Problem: rsync to NAS gives 'rsync: failed to set times on "/media/NAS": Operation not permitted (1)'

Efforts to date.

1.Initial set up was ubuntu 10.04 on stock DNS 323 NAS. Grsync would copy file names and folders to NAS but they all were 0 bytes and no data.
2.Set up FFP on NAS, installed rsync server on NAS, and retried. Grsync now copies all the files and folders,but get the 'rsync: failed to set times on "/media/NAS": Operation not permitted (1)'
3.Grsync with -t removed (does not preserve time) works without error message, but does not keep time/date on NAS backup.

Setup: NAS is automounted with CIFS:

//192.168.1.999/NAS/   /media/NAS        cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Reading at length seems to reveal that this issue is a permission problem. So my question is:

1.Is there a simple edit to my fstab file that would give me permission to save time/owner to my NAS?
2.Would I be able to use chown to modify the folder on my NAS to own it?
***if so -> pls help me with the syntax to use chown on a network drive. 
3.Do I need to edit my NAS rsync server to solve this?
4.What else would you suggest to fix this?
5.Bonus question: I have a 1 gig network/cards, my speeds are 4mb/sec. Is this a good speed for this type of network, or is this a bug of CiFS networks?

Thanks!

edit: I also tried grsync as root, but get the same error message. Thanks for looking.

---

### Post by fisheater on 2011-05-26
Ok, this has been a bear of a problem.

I've tried a few things, including:

editing my fstab to try and improve my permissions

**sec=none
 cifs    guest,sec=none,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Did not work.

**nounix
cifs    username=guest,password=,nounix,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

Did not work.

**this one works, but unable to set file times in grsync
cifs    guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0

suggestions?

Thanks! FE

---

