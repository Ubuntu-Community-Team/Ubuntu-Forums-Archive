---
title: "Copy only files of certain type"
date: 2010-02-14
forum: General Help
---

### Post by fat_man_dan on 2010-02-14
I am attempting to only copy files of a certain extension into another folder, but I am attempting to keep the full path of the files. This is to get all my video files out of my pictures directory so that they can be reprocessed for my website. I have managed to figure out ffmpeg, but want so copy all .mp4 files from /home/daniel/photos/ to /var/www/videos/ keeping the structure from the photos directory.

I have been messing around with find and sed commands to attempt to achieve this, as shown below, but I am getting stuck with what to do with the copy command....

```
#!/bin/bash
find ~/photos/hi_res/ -iname "*.mp4" > hi_res.list
cat hi_res.list | sed 's/\/home\/daniel\/photos\///' > hi_res.list
cd /home/daniel/photos/
xargs -IFILES cp -ruv FILES /var/www/videos < hi_res.list
#perform ffmpeg on /var/www/videos

```

All and any help with this would be greatly appreciated!

---

### Post by geirha on 2010-02-14
GNU cp (the version in Ubuntu) has a --parents option which also copies the parent directories of each file. Combine that with find and you get a one-liner:

```
cd ~/photos && find hi_res/ -type f -iname "*.mp4" -exec cp --parents -t /var/www/videos {} +
```

---

### Post by kaibob on 2010-02-14
> **fat_man_dan said:**
> ...I have managed to figure out ffmpeg, but want so copy all .mp4 files from /home/daniel/photos/ to /var/www/videos/ keeping the structure from the photos directory....

I've been working to learn a few of the new features of Bash 4. Working from geirha's suggestion, the globstar shell option appears to provide a workable solution for the OP (assuming karmic or later):

```
shopt -s globstar ; cd ~/photos && cp --parents **/*.mp4 ~/temp/www/videos
```

BTW, I used ~/temp as a destination directory to avoid permission issues with /var. Also, the directory structure of ~/photos is not clear to me, but it appears that the OP wants to copy all files in all directories in ~/photos.

---

