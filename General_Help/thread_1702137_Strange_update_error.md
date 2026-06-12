---
title: "Strange update error"
date: 2011-03-07
forum: General Help
---

### Post by najdorfchess on 2011-03-07
Hi all. I'm getting a strange error when I try to update my Ubuntu 10.10 32-bit version of the operating system. It runs on Inspiron-15 4GB RAM. 

[I]"Please insert the disk labeled: Ubuntu 8.10 _Intrepid Ibex_ - Release i386 (20081029.5) in drive /cdrom/"
[/I]
In the afternoon today, I accidentally deleted few sources from "other sources" tab in the Software Sources. I did it because I was annoyed by the changed name of firefox to namoroka. It's my stupidity and now I'm unable to update my system. Could anyone kindly provide me with the screen shot of "Other sources" and "Authentication" tab that are present in your ubuntu 10.10 version by default. I think I could add the sources, hopefully! 
Any help is appreciated!  Thanks  :)

---

### Post by drs305 on 2011-03-07
The message is being created because you have the 8.10 CD listed in your sources.

Open Synaptic or Software Sources (System, Administration, ...).  Go to Settings, Repositories. In the Ubuntu Software tab, in the bottom window untick the CD.

By default, the original CD used to install Ubuntu, even after online upgrades, is retained and if enabled will be requested any time you try to do an update.

Added: You can use this link to rebuild a default sources.list if required:
[http://repogen.simplylinux.ch/]("http://repogen.simplylinux.ch/")

---

### Post by najdorfchess on 2011-03-08
Thank you for your reply. Yes I did that already and I even tried putting in the CD (both 8.10 and 10.10 in different occasions), but it doesn't seem to work. I think I have accidentally deleted some software source (for update) of something that's been installed on the system and I don't know how to add it. Let me put the screen shots of my software sources tabs.

[IMG]http://img641.imageshack.us/i/screenshot3vj.png/[/IMG]
[IMG]http://img171.imageshack.us/i/screenshot2kf.png/[/IMG]
[IMG]http://img402.imageshack.us/i/screenshot1hl.png/[/IMG]
[IMG]http://img30.imageshack.us/i/screenshotct.png/[/IMG]

It would be of great help if you could refer to your original software sources repository and tell what is missing from mine. Thanks  :-)

---

### Post by najdorfchess on 2011-03-08
[http://img30.imageshack.us/i/screenshotct.png/](http://img30.imageshack.us/i/screenshotct.png/)
[http://img402.imageshack.us/i/screenshot1hl.png/](http://img402.imageshack.us/i/screenshot1hl.png/)
[http://img171.imageshack.us/i/screenshot2kf.png/](http://img171.imageshack.us/i/screenshot2kf.png/)
[http://img641.imageshack.us/i/screenshot3vj.png/](http://img641.imageshack.us/i/screenshot3vj.png/)

---

### Post by drs305 on 2011-03-08
najdorfchess,

In the second screenshot:
The CD-ROM entry has ended up in the "Other Software" tab. Untick the first entry ("CDrom with Ubuntu 8.10") and that will remove the request for the CD.

---

### Post by najdorfchess on 2011-03-08
Thank you so much. Never thought I'm this blind!  :D

---

### Post by drs305 on 2011-03-08
> **najdorfchess said:**
> Never thought I'm this blind!  :D

No problem. Normally it's not listed under this tab, but perhaps it ended up there because of the upgrade.

You can mark the thread SOLVED using the 'Thread Tools' link at the upper right of the first post.

Happy Ubuntu-ing !

---

### Post by najdorfchess on 2011-03-09
I have one more issue to be solved. As I said before that I accidentally deleted some software sources, I have been getting some errors when I update (though I could update some of the packages, but I believe it's doesn't have all the updates). The error says something like this

"
[COLOR="Blue"]***Failed to Download repository information***

[I]W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/source/Sources.gz)  404  Not Found
, W:Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/maverick/main/binary-i386/Packages.gz)  404  Not Found
, E:Some index files failed to download, they have been ignored, or old ones used instead.
[/I][/COLOR]
"

Any help?!

---

### Post by drs305 on 2011-03-09
> **najdorfchess said:**
> I have one more issue to be solved. 

These errors are being created by the "http:/launchpad.net/mozillateam" entries in the "Other Software" tab of your repository settings. They are the next-to-last entries.

The referenced repositories do not exist - the site may have moved or been removed from launchpad. To eliminate the errors, untick the two entries from the "Ubuntu Software" tab. You will be able to continue use of whatever packages you obtained from those sources but will not receive any updates to them until you find the new address.

---

