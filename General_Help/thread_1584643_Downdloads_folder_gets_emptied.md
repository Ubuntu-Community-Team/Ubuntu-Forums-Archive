---
title: "Downdloads folder gets emptied"
date: 2010-09-29
forum: General Help
---

### Post by whitething on 2010-09-29
Hey there, I'm experiencing a strange and rather unpleasant issue - my ~/Downloads directory has been emptied on reboot several times, I can't figure out any common circumstance.

I've been told on freenode that this might be some kind of ext4 (which I have as the filesystem for /home - mounted device) shortcoming.

Anyone else experienced this issue, any help?

---

### Post by robsoles on 2010-09-29
Welcome to UF.


That's an interesting problem you have there but I don't think it's anything to do with ext4 - I am responsible to my employer, myself, family and friends for quite a few PCs running Ubuntu 10.04 LTS (Desktop and Server editions) and nobody is losing files like that.


What are you using as browser/downloader? (Have you installed a download manager?)

Have you installed any software that has anything to do with cleaning or tidying or otherwise managing files?

---

### Post by whitething on 2010-10-01
> **robsoles said:**
> Welcome to UF.


That's an interesting problem you have there but I don't think it's anything to do with ext4 - I am responsible to my employer, myself, family and friends for quite a few PCs running Ubuntu 10.04 LTS (Desktop and Server editions) and nobody is losing files like that.


What are you using as browser/downloader? (Have you installed a download manager?)

Have you installed any software that has anything to do with cleaning or tidying or otherwise managing files?

Thank you)

I use Firefox and DownThemAll! plugin (however I'm pretty sure i haven't used DTA for quite a time by the moment files were gone the last time) and Chrome, no autocleaning/managing software.

---

### Post by robsoles on 2010-10-01
Do any files in your ~/Downloads directory ever persist through a restart?

Would you download something harmless and execute the line below in terminal and then restart?
```
ls >> ~/Downloads/testing.txt
```

---

### Post by whitething on 2010-10-01
> **robsoles said:**
> Do any files in your ~/Downloads directory ever persist through a restart?

Would you download something harmless and execute the line below in terminal and then restart?
```
ls >> ~/Downloads/testing.txt
```

Yeah, usually, they do persist. I've been using 10.04 for about 3 or 4 months now and there were like 3 seemingly random cases of file deletion - all considering Downloads folder.

The only thing I noticed is that one time this clearly happened after a kernel update. And i can't tell for sure, but there was another kernel update this week, don't remember whether the files got deleted after it this time.

I tried downloading files with FF and DTA and restarting while FF is open - no luck, files are still there. The test file survived, too.

Someone on freenode said it may have something to do with ext4 still being unstable, [delayed allocation]("http://en.wikipedia.org/wiki/Allocate-on-flush") and messed-up nodes.

Maybe, someone knows some sure way to cause a restart before a big chunk of delayed blocks gets written - to provoke the fail and know for sure if it exists?

Also, I tried dd'ing the home partition and recovering the files using extundelete - no nodes were found. Not that I had something of major value there, just wanted to see how it's done.

PS And yeah, I know, the good way of doing things is to rsync the home folder to an archive on another partition periodically - I'm gonna make the script and the cron task asap :)

---

### Post by searchfgold6789 on 2010-10-01
Is it possible that you could try renaming the folder and changing the default download location from ff to the newly renamed folder?

---

### Post by robsoles on 2010-10-01
> **searchfgold6789 said:**
> Is it possible that you could try renaming the folder and changing the default download location from ff to the newly renamed folder?

needn't rename ~/Downloads but could easily make a new folder and specify it as the target of the download.

---

### Post by whitething on 2010-10-01
> **robsoles said:**
> needn't rename ~/Downloads but could easily make a new folder and specify it as the target of the download.

Sure, I can do that, but who knows when the disappearance happens again.

I think I'll try that. Just in case.

---

### Post by whitething on 2010-10-03
Gee, just got deleted another time - no reboot was performed, just one time I go to Places->Downloads and it says that the link is broken - I go check out and there is no Downloads folder.

A little more info, idk if it's relevant - I have another Downloads link in favorites - the link to my storage partition's Downloads folder. That one never gets broken.

Also, I sometimes use FF private mode - when I go hunting for wallpapers on 4chan - as to not garbage FF cache with 4chan thumbnails. But then again, I do this much more often than my Downloads get deleted. Can't reproduce right now - tried switching to private and back, switching to private and closing.

Guys, maybe, there's some log I can view to figure out what's happening?

I tried doing
```
sudo cat /var/log/* | grep -i "Downloads"
```
- nothing got found.

Or, maybe, I can set up some kind of paranoid-level logging to keep track of all file operations done on my machine? I know there's a way, help me out here, please.

---

