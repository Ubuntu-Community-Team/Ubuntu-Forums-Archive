---
title: "Vista junction folders"
date: 2010-09-05
forum: General Help
---

### Post by lazychris2000 on 2010-09-05
I work for a computer repair company and I use ubuntu as my only OS on my workstation.  I never had this problem with ubuntu until installing 10.04.  Whenever I plug in a harddrive from a vista or windows 7 computer, the [junctions](http://en.wikipedia.org/wiki/NTFS_junction_point) (documents and settings, application data, my documents, etc) act like a folder, so whenever I backup a drive, Documents and Settings contains everything in the Users folder, Application data contains everything in Appdata, etc.  This makes the backups 3x bigger than they should be because there are so many copied files/folders.  When I used 9.10, the junctions showed up as just an empty folder with a shortcut emblem on them, but in 10.04 and 10.10 beta, they show up as a normal folder, complete with a copy of everything that is in the target folder.
I have found this can be overcome by just deleting the extra folders on the drive everything is being copied onto, but I have run into troubles when the customer has 200GB of pictures and movies that get copied 2 or 3 times and their external drive fills up.


I have googled around for an answer, but come up dry, so hopefully someone can make sense of what I am saying and help me find a solution.

---

### Post by Man Eating Duck on 2011-03-04
> **lazychris2000 said:**
> the [junctions](http://en.wikipedia.org/wiki/NTFS_junction_point) (documents and settings, application data, my documents, etc) act like a folder, so whenever I backup a drive, Documents and Settings contains everything in the Users folder, Application data contains everything in Appdata, etc.  This makes the backups 3x bigger than they should be because there are so many copied files/folders.
A late reply, but I'll answer in case others stumble upon this: They are presented as symlinks. 

You don't mention which backup software you use, but you have to tell it not to follow symlinks. 

Ie for rsync:
-l, --links Treat symlinks as symlinks; don't follow them

Good old cp:
-P|d, --physical|nodereference
    Don't follow symbolic links; copy symbolic rather than the files they point to. 

Most decent backup software can do this as well, you get the idea.

---

### Post by lazychris2000 on 2011-03-04
Thanks for the reply.  My boss makes us use [ycopy ]("http://www.pcworld.com/downloads/file/fid,67079-order,0/description.html") (original website is gone, but theres a download link if you wanna take a look) through wine because we can save the copy report to have a record of what was and was not copied.  As the only one in the office not using windows, I kinda get the short end of the stick.  If you can recommend a linux equivalent, I would be most grateful because it is kind of a PITA to do it this way.  Basically, all it needs is to be able to skip files that can't be copied and be able to export a list of skipped files. If it can do those 2 things, my boss won't have any room to bitch at me. Optional (just to make MY life easier) would be the ability to have a blacklist of files (for blocking pagefile, temp folders, etc).

I do feel kinda dumb for not figuring out that they are just sym links.

---

