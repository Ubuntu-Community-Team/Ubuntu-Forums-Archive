---
title: "How to check what blocks of my drive a file takes"
date: 2010-06-11
forum: General Help
---

### Post by josephellengar on 2010-06-11
I just upgraded to kernel 2.6.34 and want to test if trim is working.  To do this I'd like to do the following:

1) create a large file ~20+ mb
2) figure out what blocks of my fs the file takes up
3) delete the file
4) check if there is residual data in those blocks

What commands would I use to do steps 2 and 4?  And note that step 4 has to check at the hard drive level if there is data, not if it is just marked as being empty/not empty.  Thank you very much for your help.

---

### Post by john newbuntu on 2010-06-12
Perhaps there are other ways to do this.  The hard part is that when the file is truncated/deleted, part of its space could be taken up by another file, even though the SSDs peform wear leveling.  So, I suggest doing this test in a little container.  What I mean by that is to create your own little ext4 filesystem in a file and then inspect it.  Here is an overview of the steps, although I'll let you fine tune it:

dd if=/dev/zero of=~/testfile count=20480 bs=1024      ----------->[create a 20MB file]
losetup /dev/loop0 ~/testfile                                          ----------->[set it up as a loop type]
mke2fs -t ext4 /dev/loop0                                             ----------->[create an ext4 type fs]
mkdir ~/mymnt ----------->                                                               [a convenient mountpoint]
mount /dev/loop0 ~/mymnt                                               ----------->[mount]
cp somehugefile /mymnt                                                   ----------->[mega copy]
ls -al ~/mymnt                                                                 ----------->
[list]
dd if=~testfile | xxd ----------->                                                       [fs as hexdump - ascii values]
rm ~/mymnt/somehugefile ----------->                                               [remove the huge file]
dd if=~testfile | xxd ----------->                                                       [post-mortem of the fs.  This is where you would check the bytes]

Cleanup:
umount ~/mymnt
losetup -d /dev/loop0
rm ~testfile
rmdir ~/mymnt

Please garnish with sudo as appropriate or run it as root in a separate directory. If /dev/loop0 is in use /dev/loop1 and so on.

---

### Post by dcstar on 2010-06-12
> **rossholley said:**
> I just upgraded to kernel 2.6.34 and want to test if trim is working.  To do this I'd like to do the following:

1) create a large file ~20+ mb
2) figure out what blocks of my fs the file takes up
3) delete the file
4) check if there is residual data in those blocks

What commands would I use to do steps 2 and 4?  And note that step 4 has to check at the hard drive level if there is data, not if it is just marked as being empty/not empty.  Thank you very much for your help.

```
man debugfs
```

---

### Post by josephellengar on 2010-06-12
> **john newbuntu said:**
> Perhaps there are other ways to do this.  The hard part is that when the file is truncated/deleted, part of its space could be taken up by another file, even though the SSDs peform wear leveling.  So, I suggest doing this test in a little container.  What I mean by that is to create your own little ext4 filesystem in a file and then inspect it.  Here is an overview of the steps, although I'll let you fine tune it:

dd if=/dev/zero of=~/testfile count=20480 bs=1024      ----------->[create a 20MB file]
losetup /dev/loop0 ~/testfile                                          ----------->[set it up as a loop type]
mke2fs -t ext4 /dev/loop0                                             ----------->[create an ext4 type fs]
mkdir ~/mymnt ----------->                                                               [a convenient mountpoint]
mount /dev/loop0 ~/mymnt                                               ----------->[mount]
cp somehugefile /mymnt                                                   ----------->[mega copy]
ls -al ~/mymnt                                                                 ----------->
[list]
dd if=~testfile | xxd ----------->                                                       [fs as hexdump - ascii values]
rm ~/mymnt/somehugefile ----------->                                               [remove the huge file]
dd if=~testfile | xxd ----------->                                                       [post-mortem of the fs.  This is where you would check the bytes]

Cleanup:
umount ~/mymnt
losetup -d /dev/loop0
rm ~testfile
rmdir ~/mymnt

Please garnish with sudo as appropriate or run it as root in a separate directory. If /dev/loop0 is in use /dev/loop1 and so on.

I tried this, but it seems that the ext4 fs that you are making here is not made with the discard option, which tells it to trim.  Also, dd if=~testfile | xxd ----------->  tells me that ~testfile does not exist.  Any suggestions?  Thanks for the great tutorial.

---

### Post by john newbuntu on 2010-06-13
Typo, my bad. It should be ~/testfile.
Also in the mke2fs command use the "-k" option to keep the blocks

---

### Post by josephellengar on 2010-06-13
The two files are identical.  I guess that means that the trim isn't working?  But I didn't use the -k option.  I wasn't quite sure what you meant by that and dd spat something out at me when I tried it.  Oh well, thanks for the help.

---

