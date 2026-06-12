---
title: "Help with corrupted directory"
date: 2010-03-12
forum: General Help
---

### Post by Dr Small on 2010-03-12
First, let me give a little bit of background information:

This is a USB shared drive, with an ext3 partition. The partition is located at /dev/sdb1. I use Samba to share /media/tiga1000/samba/public, and everyone on the network can add/delete files to it. Specifically, this is our media drive, and we upload a lot of pictures to it, since me and my sister are amateur photographers.

Under /public/images/camera_pictures/2010, I have 3 directories. 01_january, 02_february, and 03_march. The directory that has been corrupted is 03_march, and when I say corrupted, I mean that I can not open it. It acts as a unknown file type that can't be opened.

Here is the file properties of it:
```
 drsmall@mycroft:/media/tiga1000/samba/public/images/camera_pictures/2010$ ls -lah
total 960K
drwxr-xr-x  4 nobody nogroup 4.0K 2010-03-11 21:22 .
drwxr-xr-x  5 nobody nogroup 4.0K 2010-02-18 20:19 ..
drwxr-xr-x 14 nobody nogroup 4.0K 2010-01-31 11:57 01_january
drwxr-xr-x 10 nobody nogroup 4.0K 2010-02-23 15:47 02_february
-r--r--r--  1 nobody nogroup 938K 2010-03-11 15:46 03_march

```

I'm not sure how I should go about recovering it. Somehow it lost it's **d**irectory switch. Should I unmount the drive and run fsck on it? I would like to be able to recover these images, if it is at least possible! Any suggestions would be appreciated!

---

### Post by cjhabs on 2010-03-12
I would back it up first and then run fsck. If fsck finds a problem, sometimes the fix involves deleteing a lot of clashing inodes. I suspect that this is what will happen to you in this case.

---

### Post by SlugSlug on 2010-03-12
Directorys need to be executable 
cd to directory and 

```
chmod 777 03_march
```

---

### Post by Dr Small on 2010-03-12
Well, I ran fsck on the partition, and it didn't fix the problem, and I chmod'ed the "file" to 755 (as is what the other ones are), and it's just an executable file now, nothing more. Hmm.

---

### Post by SlugSlug on 2010-03-12
```
cat 03_march
```


maybe it is just a file?

---

### Post by rnerwein on 2010-03-12
hi
i think that slugslug is on the wright way ( cause of the size of 03_march ). 
what does: file 03_march - will tell you. i guess it's an archive.
ciao

---

### Post by gmargo on 2010-03-12
Oh come on.  The directory is not corrupted.  You made a mistake.  You copied a file to a non-existent directory, so the copy changed the name of the file.  Do a "file 03_march" - I bet it says jpeg (or whatever image format).

---

### Post by Dr Small on 2010-03-12
> **gmargo said:**
> Oh come on.  The directory is not corrupted.  You made a mistake.  You copied a file to a non-existent directory, so the copy changed the name of the file.  Do a "file 03_march" - I bet it says jpeg (or whatever image format).
Sure enough. It was an image. (It wasn't me copying pictures... it was my sister, and then I have to dig through to see what she did wrong :S). Right now, I'm attempting to recover a bunch of inodes from lost+found, and put them back on the file server.

---

