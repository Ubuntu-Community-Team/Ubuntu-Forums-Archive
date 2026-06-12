---
title: "Permanently deleting files, and making them unrecoverable"
date: 2012-01-22
forum: General Help
---

### Post by m5K5n on 2012-01-22
I've deleted a file that I'd like to be unable to be recovered.  However, all the guides I've found are for before a file has been deleted.

So, how can I ensure that the deleted data is unrecoverable?

---

### Post by alphacrucis2 on 2012-01-22
> **m5K5n said:**
> I've deleted a file that I'd like to be unable to be recovered.  However, all the guides I've found are for before a file has been deleted.

So, how can I ensure that the deleted data is unrecoverable?

Maybe bleachbit. It has an option to blitz unused file system space (which would include space that was occupied by files that have been deleted from the trash. It isn't selective though - it will do all free space so will take a while.

---

### Post by xyzzyman on 2012-01-22
BleachBit is an easy way. Just select for it to wipe free space.

EDIT: Like he said. lol. I wrote that, walked away to make a sandwich, came back and submitted only to find someone beat me to it.

---

### Post by pr3zident on 2012-01-22
i think you should look in shred

---

### Post by xyzzyman on 2012-01-22
> **pr3zident said:**
> i think you should look in shred

As the original poster stated, he has already deleted the files. shred works on files before you've actually deleted them.

---

### Post by pr3zident on 2012-01-22
> **xyzzyman said:**
> As the original poster stated, he has already deleted the files. shred works on files before you've actually deleted them.

ok great 
m5K5n - the next time you want a file unrecoverable i think you should use shred is that better xyzzyman ?

---

### Post by m5K5n on 2012-01-23
I downloaded BleachBit through the Ubuntu Software Center.  But I'm worried about some of the dialogue boxes that come up when I click on certain operations.

---

### Post by xyzzyman on 2012-01-23
If you want, you can just uncheck everything except for 'free disk space'. If the file was in your home folder you can run bleachbit as a normal user. If it's in a system folder then run bleachbit as root.

---

### Post by m5K5n on 2012-01-23
> **xyzzyman said:**
> If you want, you can just uncheck everything except for 'free disk space'. If the file was in your home folder you can run bleachbit as a normal user. If it's in a system folder then run bleachbit as root.

I run it by clicking the icon in the applications menu.  I suppose that's as a normal user, since there's also a "as root" version?

---

### Post by xyzzyman on 2012-01-23
Yes, that's why both icons are there. If you can achieve what you want by running as a regular user then that is the way you should always go. I use the 'as root' icon to clean up apt, log files, remove languages I don't need. Things that the normal user normally can't delete. As root you can mess things up by going to far (Deleting your main language would probably not be good.) Also be careful on the web browser sections. Chrome likes to use as much HDD as you give it for cache so I clean it every so often, but I make sure not to check off having it delete my history or cookies.

---

### Post by Paqman on 2012-01-23
You can use the command sfill to wipe all free space on a drive. I'd be wary of using Bleachbit in case it did multiple writes, which is pointless and could lead to a very, very long wait on a large drive with lots of free space.
```
sudo sfill -l -l -v /mount/point
```
This command will do a single pass with random data. Include the flag -z if you just want to wipe with zeros. Sfill is part of [secure-delete]("apt:secure-delete").

---

### Post by xyzzyman on 2012-01-23
BleachBit is doing the same thing. Just one swipe which is all that's needed.

---

### Post by dragonfly41 on 2012-01-23
Depends on how sensitive the data is .. forensic analysis can still recover apparently scrubbed files.

[http://www.brown.edu/cis/policy/datarmv.php](http://www.brown.edu/cis/policy/datarmv.php)

---

### Post by Cheesemill on 2012-01-23
> **dragonfly41 said:**
> Depends on how sensitive the data is .. forensic analysis can still recover apparently scrubbed files.

[http://www.brown.edu/cis/policy/datarmv.php](http://www.brown.edu/cis/policy/datarmv.php)


Not true.

[http://www.nber.org/sys-admin/overwritten-data-guttman.html](http://www.nber.org/sys-admin/overwritten-data-guttman.html)

---

### Post by 3rdalbum on 2012-01-23
PLEASE stop recommending 'shred'. It works fine for erasing free space, but it is NOT reliable for deleting a single file for two reasons:

1. The changes to files on ext partitions may possibly be saved to another physical part of the disk, leaving the original version INTACT.

2. Newer filesystems like btfs do versioning. Shred will not be able to delete older versions of the file.

The best solution is encryption. Encrypt your home directory and even deleted files will still be encrypted and inaccessable for anyone without the decryption key.

Finally, if you want to run Bleachbit to overwrite all the free space, you MUST run it as root. The last 5% of the disk capacity can only be written to by root, and you want to make sure that every non-allocated sector is overwritten in case that's where the original copy of your file was written to :-)

---

### Post by xyzzyman on 2012-01-23
> **3rdalbum said:**
> Finally, if you want to run Bleachbit to overwrite all the free space, you MUST run it as root. The last 5% of the disk capacity can only be written to by root, and you want to make sure that every non-allocated sector is overwritten in case that's where the original copy of your file was written to :-)

+1. I'd forgotten about that.

---

