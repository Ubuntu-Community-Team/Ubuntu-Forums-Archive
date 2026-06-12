---
title: "Macbookpro mounted HFS, now what"
date: 2011-05-09
forum: General Help
---

### Post by disappearedng on 2011-05-09
Hey everyone, 

I created a Data partition in my mac based on HFS+ without journaling (I did the diskutil disable-journaling command in mac). 

Now I have this in my /etc/fstab: 

/dev/sda3       /mount/Data     hfsplus defaults        0       0


Now when I start my computer, /dev/sda3 is automatically mounted. 

When I navigate into the partition, I am getting the following:

```
disappearedng@disappearedng-MacBookPro:~/Data$ ls -l -h -a
total 20K
drwxrwxr-x 1  501 dialout   14 2011-05-09 03:12 .
drwxr-xr-x 4 root root    4.0K 2011-05-09 17:19 ..
drwx------ 1  501 dialout   24 2011-05-09 03:30 Downloads
drwx------ 1  501 dialout   28 2011-05-09 17:11 Dropbox
-rw-r--r-- 1  501 dialout  13K 2011-05-09 03:05 .DS_Store
drwx------ 1 root dialout    4 2011-05-09 17:15 .fseventsd
dr-xr-xr-t 1 root root       2 2011-05-05 19:32 .HFS+ Private Directory Data?
drwxr-xr-x 1  501 dialout    5 2011-05-07 02:47 Music
drwx------ 1 root dialout    3 2011-05-05 19:32 .Spotlight-V100
drwxrwxrwt 1  501 dialout    3 2011-05-08 16:50 .TemporaryItems
drwxr-xr-x 1  501 dialout    3 2011-05-06 03:22 Torrents
d-wx-wx-wt 1 root      99    3 2011-05-08 02:46 .Trashes
drwxr-xr-x 1  501 dialout    4 2011-05-09 03:12 wallpaper
```

Problem is: 
I can't navigate into Dropbox folder due to insufficient permission. 

I am very tempted to just do a chmod 755 on the entire drive but I know that might REALLY mess things up.

What are some strategies to this?

---

