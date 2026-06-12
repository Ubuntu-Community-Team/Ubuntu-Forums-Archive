---
title: "data recovery experiment using dd"
date: 2009-10-06
forum: General Help
---

### Post by ttallos on 2009-10-06
I loaded windows to a small drive and erased 4 files and then deleted them out of the trash can. Then I made a dd image of that (3.2G) and now I want to try to mount the image or use some other utility in ubuntu to get those 4 files. Here is the command to mount the image that I used:
sudo mount -o loop /path/to/somefile.img /media/image
I was thinking testdisk or photorec but not sure how to do this. Cause I am a noob.

---

### Post by cdenley on 2009-10-06
To recover deleted files, you want to access the image directly, not mount it.
```

sudo apt-get install ntfsprogs
man ntfsundelete

```

---

### Post by rbc on 2009-10-06
You created an image file of the Windows partition, great. Keep it as a backup. After you have photorec/testdisk installed, go to terminal and type:
sudo photorec

The Windows partition does not need to be mounted.

Photorec will then ask the following questions:
-which drive?
-what partition table type? Probably Intel
-which partition on the hard drive you selected?
-file system type?
-Free space or whole partition?
-where you want to store the recovered files (Hint: Do not recover the files TO the partition you are trying to recover FROM)

There are many ways to do this, but here’s the easiest, in my opinion…..If you really want to have some fun, google “data carving”. You’d essentially be doing, manually, what photorec does for you

---

### Post by ttallos on 2009-10-06
thank you for your advice I will try each one. I didn't know that ubuntu could be used as a data recovery feature till 1 week ago. I have been using ubuntu for 5 years and love it!

---

