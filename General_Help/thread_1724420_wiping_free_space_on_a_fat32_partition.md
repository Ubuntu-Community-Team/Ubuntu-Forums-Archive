---
title: "wiping free space on a fat32 partition"
date: 2011-04-08
forum: General Help
---

### Post by Bazon on 2011-04-08
Hello!

I'd like to wipe free space on a fat 32 partition, momentary by doing

```
cat /dev/urandom >garbage
```

The problem is:
That stops each time the file is 4GB big, as this is the maximum supported filesize for fat32 partitions. 
So I redo the command, only writing now to "garbage2" or so.

Is there any more elegant way to do that? Maybe by script which automatically generates new file names, until the disc is full? 

Thanks!

---

### Post by Grenage on 2011-04-08
```
sudo apt-get install secure-delete
```

This suite contains several programs, one being *sfill*, which will wipe all the space marked as empty on your hard drive.

---

### Post by Bazon on 2011-04-08
Unfortunately, *sfill* has the same problem: it creates and deletes a 4GB file, but doesn't wipe the whole rest of the fat32 disc.
(According to my test)

but thanks anyway.

any other solution?

---

### Post by Grenage on 2011-04-08
What about a loop, which keeps creating new files and incrementing the names?  The only thing I'm unsure of would be the loop exit criteria, but that could be gained through the *df* command (when all space is gone, stop).

---

### Post by Bazon on 2011-04-08
Yes, a loop would be fine.
Unfortunately, I have no idea for the syntax of that. could someone give me a hint where to start looking? :-)

---

### Post by Grenage on 2011-04-08
Something like this?

```
while (( $(df /dev/sda5 | awk 'NR==2{print $4}') > 100 )); do
  cat /dev/urandom > /mnt/partition/$(date +%y%m%d%M%S)
done
```

Where 100 would be the byte count it might stop at, /dev/sda5 is the partition, and /mnt/partition is the mounted partiton.  I haven't got a drive to test this on right now, but I could do on Monday.

---

### Post by Bazon on 2011-04-08
Thanks, that works! :-)

---

### Post by Grenage on 2011-04-08
Glad to hear it!

---

