---
title: "Search for content in files"
date: 2010-03-05
forum: General Help
---

### Post by nmyrick on 2010-03-05
Help!  I need the ability to search for file content in documents and spreadsheets and I need to be able to do this from the folder level.

When I hover my mouse over the "search" button in the file browser toolbar, it says that it can "locate documents and folders on this computer by name or content," but that is ***not*** the case.  It can only locate documents and folders by name.  Is there something I need to download that will allow me to do this?  I have nautilus file manager.

Thanks,
nmyrick

---

### Post by roger_1960 on 2010-03-05
Hi

Have a look at this thread:

[http://ubuntuforums.org/showthread.php?t=986315](http://ubuntuforums.org/showthread.php?t=986315)

---

### Post by Morbius1 on 2010-03-05
Open Terminal
Type **gnome-search-tool**

When it opens click on "Select more options" 

You'll be able to search by file name, content, date, size, and color.

Ok, I made up the thing about color ;)

---

### Post by nmyrick on 2010-03-05
Thank you Morbius1!  With the gnome-search-tool command, I was able to create a custom file search launcher in my AWN Desktop Toolbar that does the same thing.  In case you are not familiar with AWN, it is in your Ubuntu Software Center in 9.10, and it is a launcher bar like the bar that is at the bottom of the desktop of a Mac.  It is really cool!

Thanks,
nmyrick

---

### Post by nmyrick on 2010-03-05
Thanks, but the command gnome-search-tool still doesn't work.  Yes, it opens a new window with a search tool that is supposed to find the text in files, but it doesn't work for .doc, .docx, .odt, .xls, and .xlsx files. It only works for .txt files, as far as I can tell.

---

### Post by Morbius1 on 2010-03-06
That's interesting. After reading your post, I just created a .doc file with a specific work in it and placed it on my desktop. I then brought up gnome-search-tool, pointed it to my desktop and searched for anything that had that word in it. It found the .doc file.

Maybe it's because I created the .doc file from OpenOfffice. I would think that it would be compatible enough with a .doc created from MS Office.

---

### Post by sgage on 2010-03-06
Try recoll (available in the standard repos). It is very fast and thorough, and can deal with all sorts of files if you install various helpers. The cool thing is that after indexing, it will tell you what files it encountered that require a helper, and you can then install it.

It is my favorite indexed search tool for Linux.

---

### Post by nmyrick on 2010-03-06
Thank you.  I just installed trackerd, which according to this post at [http://ubuntuforums.org/showthread.php?t=986315](http://ubuntuforums.org/showthread.php?t=986315), is one that works well with Ubuntu. However, I've noticed that it has to restart the tracker from zero every time I restart my computer, and it has never completed tracking.  

Do you know if it will store the results once it completes tracking the first time, or will it restart every time?  If it has to restart the tracker every time, then that will be a pain, because it says there are 22,000+ files that it needs to track, and it says that it will take about two hours to complete.  However, it doesn't seem to affect my computer's performance.

Thanks,
nmyrick

---

### Post by nmyrick on 2010-03-06
Correction on my last post.  Actually, Trackerd is commonly refered to as MetaTracker, and apparently came with earlier versions of Ubuntu.  I seems to work well so far with 9.10, and it even show the status and an icon right in the system status tool bar. Heres the link.

[https://help.ubuntu.com/community/MetaTracker](https://help.ubuntu.com/community/MetaTracker)

It also says that it will take a long time the first time you run it. I guess I just need to let it complete the scan.

Thanks,
nmyrick

---

### Post by nmyrick on 2010-03-06
After trying MetaTracker in Karmic, I've noticed that the indexing process seems to hang after a few minutes.  It says that it is still indexing, but after a while it stops showing forward progress.  I'm trying recoll right now, I'll let you know what I think.

Thanks,
nmyrick

---

### Post by DZ* on 2010-03-26
You can install "google desktop" for searching file contents. However, there is also a way to do quick searches from nautilus, provided you enabled beagle or/and tracker support.

Currently, this is disabled in Ubuntu for some reason. But it is fairly easy to recompile nautilus with the support:

```
sudo apt-get install beagle beagle-xesam beagle-dev libbeagle1 libbeagle-dev libslab0 wv catdoc odt2txt poppler-utils
sudo apt-get build-dep nautilus
sudo apt-get install build-essential tracker tracker-utils tracker-search-tool libtrackerclient-dev libtracker-gtk-dev fakeroot 

sudo apt-get source -b nautilus
sudo dpkg -i libnautilus-extension*.deb nautilus*.deb
killall nautilus

```

Now, once this is done (you have to re-login for beagled and trackerd to start), and if you want to search with tracker from nautilus (with Ctrl-F), you have to stop beagle first: ```
beagle-shutdown
``` Otherwise nautilus will use beagle.

One thing to watch for: next run of Software Update will try to replace your custom built nautilus with the one from the repos, so you'd have to un-click nautilus* and libnautilus*.

There appears to be a limited support for searching tracker tags in nautilus (which I discovered by stupidly trying tag:XYZ and it worked) -- [http://forums.fedoraforum.org/showthread.php?t=221435](http://forums.fedoraforum.org/showthread.php?t=221435)

---

