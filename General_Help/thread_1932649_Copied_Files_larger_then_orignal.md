---
title: "Copied Files larger then orignal"
date: 2012-02-27
forum: General Help
---

### Post by thinkdez on 2012-02-27
So here is my issue and I find it rather odd.  I have a disk that has reached its capacity.  So I went an bought a new disk with larger capacity and I am trying to transfer the 1TB of data to it but when it gets to the destination drive the data has a larger size then the original.  The first time I tried this the data was 1.3TB and growing when the original data size is 770GB.  I wiped it and restarted and it looks like I am heading down the same path.  Anybody have any ideas on what might be happening?

BTW I am copying via NFS.

---

### Post by conradin on 2012-02-27
Um, I have some ideas. How is the former hard drive disk health? are there numerous bad sectors, or evidence of File System Corruption? What are the Filesystem types? 

What are teh block sizes of the old hard drive and what is it on the new hard drive?

To find block size for a partition:
```
$ sudo /sbin/dumpe2fs /dev/<partition> | grep 'Block size'
```

---

### Post by 3rdalbum on 2012-02-27
Is most of the space taken up by small files or big files? If it's small files then perhaps the different minimum block sizes of the disks are different, and each small file is being expanded to fill the larger minimum block size.

Just a theory.

---

### Post by thinkdez on 2012-02-27
Hi everyone,
           It seems as though the block size is the issue here.  It is what I first thought but when the disk capacity went to 1.4TB from 770GB I thought it was too far off to be that.  The file copy completed and I only have a 5GB difference.  With the data that I have on this drive I can see it being strictly block size differences. 

Thanks for all your responses.

---

