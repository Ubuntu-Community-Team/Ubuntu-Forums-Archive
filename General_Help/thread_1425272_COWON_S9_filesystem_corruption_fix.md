---
title: "COWON S9 filesystem corruption fix"
date: 2010-03-08
forum: General Help
---

### Post by OrangeVixen on 2010-03-08
I recently mounted my COWON S9 (16GB) to a Mac to "transport" (copy) some files.

Then brought it back to my Linux and mounted it to copy the files over to my Linux.

I deleted the said files on my COWON S9 but then noticed a problem the next day. Linux (I was using Ubuntu Jaunty) mounted it as read-only, and copy or deleting any files to/from it always got either a read only error or an input output (I/O) error.

I was considering reformatting it but I was able to fix it using dosfsck.

# dosfsck -r -v /dev/sdh

It detected an unterminated chain and asked to correct it and I said yes.

Note that my COWON S9 is always detected as /dev/sdh but it may vary on your computer, plug it in and run:

# mount

I typically get:

/dev/sdh on /media/COWON S9 type vfat (rw,nosuid,nodev,uhelper=hal,shortname=mixed,uid=1000,utf8,umask=077,flush)

Now I'm hoping this does not happen to me again and I don't know if dosfsck will always fix the problem. I do know that other users have had problems with the COWON S9 on Macs so the filesystem might have gotten corrupted when it was mounted on the Mac.

Note that I also had to run dosfsck a couple of times to get it fixed.

---

