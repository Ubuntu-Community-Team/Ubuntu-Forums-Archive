---
title: "Undelete in Ubuntu?"
date: 2009-09-29
forum: General Help
---

### Post by Rytron on 2009-09-29
Hi.
Is it possible to undelete files in Ubuntu such as [this program]("http://www.filehippo.com/download_recuva/") does in Windows?
Thanks.

---

### Post by Rytron on 2009-09-29
I found this program:

```
foremost
```

How would I retrieve an file titled cat.gif that was accidentally deleted from my desktop?

---

### Post by pmlxuser on 2009-09-29
Photorec can do that only differnce is photorec is text based.

[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

---

### Post by cdenley on 2009-09-29
Photorec can recover some deleted files, I believe including gif images. However, assuming you're using ext3 or ext4, file meta-data such as name and location are erased, so you will not be able to search by filename, only recover all gif images (deleted or not). It's not in "Trash", right?

Also, I think you cannot use photorec on currently mounted filesystems. It is part of the testdisk package in the repos.

---

### Post by automaton26 on 2009-09-29
I'd recommend a proper read of the manual first really...

```
man foremost
```

...but quickly, from memory, I think you need to:

1) Determine the device (/dev) that corresponds to the file's partition:

```
sudo fdisk -l
```

2) Use foremost to restore gifs from /dev/???? and put them in a particular folder, for example:

```
foremost -vT -t gif -i /dev/??? -o ~/Downloads/foremost
```


NOTE: If anyone wanted to undelete anything really critical, it would be important to turn the machine off, detach that drive, and plug it into a separate machine. Then they could just get read-only access to it, before trying any undelete process. That's because, at any time, the OS can be writing temporary files to the filesystem which greatly increases the chance of the space being overwritten permanently.

---

### Post by Rytron on 2009-09-29
Thanks guys. This would be especially handy if I or someone else ever deleted very important data that did not have a backup copy.

I will give foremost a shot.

---

### Post by usererror on 2010-11-22
I just made a major blunder and want to give "two thumbs up" to "PHOTOREC"

I accidentally deleted 10GB worth of photos. The .Trash-1000 folder was empty. I installed the APT package "testdisk" and used "photorec" to scan for lost files and it got back 99% of my files back. I am quite pleased. Recovery time was several hours, but it worked great!

The only downside was that the file names were not the same as before but the EXIF data from the .jpg files was still intact.

---

