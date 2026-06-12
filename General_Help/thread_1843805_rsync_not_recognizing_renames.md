---
title: "rsync not recognizing renames"
date: 2011-09-14
forum: General Help
---

### Post by Brad_J on 2011-09-14
Hi all, I'm having a bit of a problem with rsync. I'm using it to sync files from my dropbox folder to my local drive and vice versa on my linux machine; as in I can make changes to either side and it'll copy them over if I run my bash script. The problem that I'm having is that I'm getting a whole bunch of duplicate folders when I rename anything, for example if I had a folder called "Folder1" and it had 100 MB in it and I wanted to rename it to "Folder2" (I'm not known for my creativity) I would then have two folders with 100MB each in them. This is a problem for a number of reasons: Dropbox size limits, Time spent syncing, confusion with two similarly named folders, etc. I was wondering if there was some way to have it recognize renames or at least copy over the newer folder and delete the old one. This is my bash script for syncing my files:
```

rsync -r -t -v --progress -u --modify-window=1 /media/Storage/workspace/ /media/Storage/Dropbox/workspace/
rsync -r -t -v --progress -u --modify-window=1 /media/Storage/Dropbox/workspace/ /media/Storage/workspace/
rsync -r -t -v --progress -u --modify-window=1 /media/Storage/BCIT/ /media/Storage/Dropbox/BCIT/
rsync -r -t -v --progress -u --modify-window=1 /media/Storage/Dropbox/BCIT/ /media/Storage/BCIT/

```
I dual boot so I also run Windows occasionally, hence the "modify-window=1" for the time discrepancies that I've been told occur when copying between linux and windows machines. Any help for this is appreciated, thanks for your time.

-Brad

---

### Post by SecretCode on 2011-09-14
I don't know of any such capability in rsync. It doesn't keep any record of moves or renames or file hashes, which would probably be necessary for this kind of capability.

But dropbox can do this (I've observed that dropbox sync is v fast when you've just renamed a directory or moved some files). So it might be more efficient to get dropbox to sync directly to your local drive. (If it's a removable backup drive this won't help so much.)

---

### Post by Brad_J on 2011-09-14
> **SecretCode said:**
> I don't know of any such capability in rsync. It doesn't keep any record of moves or renames or file hashes, which would probably be necessary for this kind of capability.

But dropbox can do this (I've observed that dropbox sync is v fast when you've just renamed a directory or moved some files). So it might be more efficient to get dropbox to sync directly to your local drive. (If it's a removable backup drive this won't help so much.)

I guess I was kind of misleading... Right now, Dropbox has a location on my Storage partition and my backup has a location elsewhere on the same partition. It's fine to work straight out of my Dropbox folder, but I like to have an extra backup in case I screw up something, and since Dropbox automatically syncs my files to the latest versions as soon as I get online, it's possible for me to lose a lot of progress in any work I have. I probably seem like I'm way over-doing it for keeping my files safe, but, I don't like relying on Dropbox alone to keep everything backed-up and safe. Thanks for responding, though!

EDIT: Basically, I want the information kept in two locations on my computer

---

### Post by SecretCode on 2011-09-14
I thought you might be doing something like that.

But then why are you syncing from the backup into your dropbox folder? Wouldn't it be better to sync one way and
(a) if you ever need to recover a file, do it manually
(b) occasionally clean out old duplicate files in the backup using rsync --delete option (when you are confident you don't need any of them)

---

### Post by Brad_J on 2011-09-14
> **SecretCode said:**
> I thought you might be doing something like that.

But then why are you syncing from the backup into your dropbox folder? Wouldn't it be better to sync one way and
(a) if you ever need to recover a file, do it manually
(b) occasionally clean out old duplicate files in the backup using rsync --delete option (when you are confident you don't need any of them)

I could do that, but I usually end up working out of the local file from Windows on the same machine. Dropbox seems to have this problem where I have to resync my folder every time I switch from Windows to Ubuntu, and I end up with a bunch of conflicting copies if I work straight out of there. I could try to fix that problem instead and use your suggestion, as it makes a lot of sense, but if I'm unsuccessful I guess I'm going to have to deal with long sync times and deleting my renames. Thanks for your help.

-Brad

---

