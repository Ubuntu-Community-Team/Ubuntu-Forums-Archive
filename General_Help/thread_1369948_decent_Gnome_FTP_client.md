---
title: "decent Gnome FTP client?"
date: 2010-01-01
forum: General Help
---

### Post by michaelzap on 2010-01-01
I had to use Vista to make a Flash file today, so I uploaded some files with WinSCP for the first time in months. I'm still amazed that there isn't a single decent GUI FTP client available for Gnome. I'd love for someone to prove me wrong, but so far I can't find anything that meets my (fairly basic) requirements:

[LIST]
[*]doesn't crash or time out frequently
[*]site/bookmark manager with local and remote directories saved
[*]automatic transfer mode
[*]synchronized directory browsing
[*]keep-alive, passive mode
[*]change permissions/owner
[*]remote file editing
[*]resuming of large file transfers
[*]ability to move files on the remote server
[*]SSH/SFTP, etc.
[*]multiple tabbed sessions, FXP (would be nice)
[*]comparison and synchronization of local and remote folders (also would be nice)
[/LIST]

Right now I make do with a combination of FireFTP and Filezilla. FireFTP works well enough for most of my transfers, but it doesn't allow me to move files on the remote server (plus now that I've started using Chrome as my main browser, it's gone from convenient to bloated). Filezilla's interface reminds me of Windows 95, and it doesn't do synchronized browsing unless you tell it to and frequently refuses to overwrite files that have changed (among other annoying quirks).

Can't we do better than this in Linux?

Anyone found a better alternative?

---

### Post by gordintoronto on 2010-01-01
gFTP works fine for me.  It might not have all the features you desire, though.

---

### Post by michaelzap on 2010-01-01
> **gordintoronto said:**
> gFTP works fine for me.  It might not have all the features you desire, though.

It doesn't, and it also crashes on me fairly often. I'd love it if the default Gnome FTP client worked well. That would be ideal for me, since I don't want anything fancy just fully-functional.

---

### Post by gsmanners on 2010-01-01
If gFTP is "crashing" on you then that surely means there's a problem with your network, not with gFTP. I've been using that client for years, and it is bar none the best FTP client period.

---

### Post by dcstar on 2010-01-01
> **gsmanners said:**
> If gFTP is "crashing" on you then that surely means there's a problem with your network, not with gFTP. I've been using that client for years, and it is bar none the best FTP client period.

+1, it works fine on a stable system (and has for years).

---

### Post by michaelzap on 2010-01-01
> **gsmanners said:**
> If gFTP is "crashing" on you then that surely means there's a problem with your network, not with gFTP. I've been using that client for years, and it is bar none the best FTP client period.

I'm not convinced of that (since I've seen a lot of other complaints of gFTP crashing), but I'll accept it as your experience. It doesn't do automatic transfer mode, synchronized directory browsing, or remote file moves, so it's not really in the running for something that I could use on a regular basis anyway. It's interface is actually a bit worse than Filezilla's imho.

Any other options that do at least most of the things on my list?

---

### Post by morningboat on 2010-01-02
You can have a look at this list. [http://www.gnomefiles.org/subcategory.php?sub_cat_id=44](http://www.gnomefiles.org/subcategory.php?sub_cat_id=44)
Some of the most popular one have all of your needed features, such as CrossFTP Pro.

---

### Post by michaelzap on 2010-01-02
Thanks for the link. I haven't tried some of the apps on this list, so I'll check them out. I might have to pony up $25 for CrossFTP Pro, but they have a 30-day trial to see if I like it first.

---

### Post by michaelzap on 2010-01-03
OK so I checked out the FTP clients that I wasn't already familiar with, and I was underwhelmed by most of them. The ones that looked promising (CrossFTP, IglooFTP) were both commercial Java apps, and I try to avoid using Java apps. I tried to get CrossFTP to work anyway to test it out, but for some reason it doesn't like the version of Java that comes with Karmic so I gave up.

I probably would've tried harder, but I actually discovered some new features and improvements in Filezilla 3.3.0 that I had overlooked before. It now has a tabbed interface, and it also allows you to set synchronized directory browsing on for each of your bookmarks. I used it a bit earlier today, and the bug that was forcing me to delete remote files and reupload them instead of just overwriting them also seems to have been fixed.

So all in all I might just be happy with Filezilla. I wish it used the Gnome keyring or some other secure method to store saved passwords, but I suppose I always encrypt the disk anyway so it doesn't really matter.

---

