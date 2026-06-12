---
title: "How to backup files - please help!"
date: 2009-11-07
forum: General Help
---

### Post by raafe on 2009-11-07
HI everyone, bit of a noob question i am afraid - i did have a look around on google but I am not really sure how to word my question to get good search results. Basicly I have 2 external hard drives both 500GB which I use to store my media, I want to use one drive as a backup drive - now I have installed keep and that is very easy to use so that is ok, but before I start using it I need to copy over the files from my external backup drive to my other external drive but alot of the files are the same and it would take a long time to go through and find out which files are on one and not the other.. so my question is this can I copy over ONLY the files that are in one and not the other?

I hope this makes sense to people!

Thanks for any help

Guy

---

### Post by Cuddles McKitten on 2009-11-07
You might want to look into rsync.

Or if you want to do it the quick and dirty way, you can just drag and drop in Nautilus and just choose "skip all" when prompted if you want to overwrite a file.

EDIT: I just realized you're using Kubuntu.  I'd guess KDE's file manager has a similar capability, but it might not work exactly the same.

---

### Post by profeta81 on 2009-11-07
depends what tools you're using...

if you just want to copy the files you can use at the command line:

cp -a -u SOURCE DEST

the -a option is used to aviod deferencing of the symbolic links, to copy recursively and to preserve all attributes (timestamp, ownership etc); the -u option copy files only if the timestamp of destination is older than the source timestamp (see man cp for a complete description).

I never used this command myself, so you should make a test first with a couple of mock files (try making a directory, and create some txt files in it, then copy it, chenge the files and use that command and see what happens...).

cheers ;)
Lorenzo

---

### Post by SuperSonic4 on 2009-11-07
> **profeta81 said:**
> depends what tools you're using...

if you just want to copy the files you can use at the command line:

cp -a -u SOURCE DEST

the -a option is used to aviod deferencing of the symbolic links, to copy recursively and to preserve all attributes (timestamp, ownership etc); the -u option copy files only if the timestamp of destination is older than the source timestamp (see man cp for a complete description).

I never used this command myself, so you should make a test first with a couple of mock files (try making a directory, and create some txt files in it, then copy it, chenge the files and use that command and see what happens...).

cheers ;)

Lorenzo

Dolphin and Krusader will ask you whether you want to skip all or not - konqueror probably will too

You could also use cp with the -u flag

```
cp -Ruvp src_folder dest_folder
```

-R = Recursive - copy a directory and all it's subdirectories
-u = Update    - copy only when src is newer than dest
-v = Verbose   - tells you what's going on
-p = Preserve  - keeps the owner etc

---

### Post by raafe on 2009-11-07
Thanks everyone! Got it all sorted with your help, just using keep to back everything up now - only annoying things about keep is it doesn't have any kind of progress bar and I am backing up a good 450GB worth of data.. But i will leave it on over night and see how it's doing in the morning.

Will mark as solved.

Thanks again everyone!

Guy

---

