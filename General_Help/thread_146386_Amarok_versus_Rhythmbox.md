---
title: "Amarok versus Rhythmbox"
date: 2006-03-18
forum: General Help
---

### Post by gwilson on 2006-03-18
Anyone know why it is that Amarok cannot find some of the music on my hard drive that Rhythmbox can? I love Amarok, but have to resort to Rthymbox to find and listen too quite a bit of my music.

There isn't any way to change the Amarok search criteria, is there? It's already looking at the correct subdirectories but doesn't recognize the music files.

Thanks

GW

---

### Post by trotski on 2006-03-18
It might have something to do with Taglib.  What formats are those files in?

---

### Post by nrwilk on 2006-03-18
Are all the files of the same format?  I had to install and use amarok-xine before amarok would play mp3s and streaming audio.

```
sudo apt-get install amarok-xine
```
Then under Amarok's config, go to the engine section, and select xine from the drop-down menu instead of gstreamer.  Save the config, and see if Amarok then recognizes your files.

Hopefully it's something as simple as this.  If not, at least you've installed an engine which I've found to work much better with Amarok.  ;) 

Good luck!  :)

---

### Post by gwilson on 2006-03-18
Thanks for the suggestion, NRWILK, but I've already done all of that.

I wonder if changing the "Collection Database" would make any difference?

Anyone have any experience with that?

Thanks.

---

### Post by nrwilk on 2006-03-18
It's sucky that that didn't work.

It was more of a guess than anything else, but I figured it may help.

I hope you get it fixed, that's a frusterating problem.

---

### Post by gwilson on 2006-03-18
[QUOTE=nrwilk]It's sucky that that didn't work.

It was more of a guess than anything else, but I figured it may help.

I hope you get it fixed, that's a frusterating problem.[/QUOTE]

Well, thanks for trying, anyway.  ;-)

---

### Post by Barrakketh on 2006-03-18
Open the Collection flyout and click the Configure Folders (wrench) icon.  Make sure the folders that contain your music are selected (or a parent of those folders) and that scan recursively is checked.  If it's new music that isn't being detected, you'll need to either check "Watch folders for changes" or use Tools -> Rescan Collection to update your collection.  If your music isn't properly tagged then it might end up in a weird location even if it is in your collection.

I'm not sure how amaroK behaves, but you may need the MAD gstreamer plugin if it's not already installed.  In breezy the package is called gstreamer0.8-mad.

---

### Post by gwilson on 2006-03-18
[QUOTE=Barrakketh]Open the Collection flyout and click the Configure Folders (wrench) icon.  Make sure the folders that contain your music are selected (or a parent of those folders) and that scan recursively is checked.  If it's new music that isn't being detected, you'll need to either check "Watch folders for changes" or use Tools -> Rescan Collection to update your collection.  If your music isn't properly tagged then it might end up in a weird location even if it is in your collection.

I'm not sure how amaroK behaves, but you may need the MAD gstreamer plugin if it's not already installed.  In breezy the package is called gstreamer0.8-mad.[/QUOTE]

Thanks, but I have all that covered. There's just a difference between the way that Amarok and Rythmbox catalog their database.

***************UPDATE  ********  SOLUTION

Well, this solved MY problem, anyway.  I've had the aforementioned problem in Breezy. Then I installed Dapper in a new partition and the problem was STILL there. Then I went to the Amarok website and found that there was a version 1.4 beta available for Dapper only (not Breezy). I followed the instructions to add the repository to my Synaptic setup. Then I ran the Update Manager, and it found the new version of Amarok and installed it. So far, it works well.

AND it found all of the music that version 1.3.8 could not.  I guess that's progress. Unfortunately, this 1.4 version is only for Dapper installations, and it IS still only a beta version, so it's not for everyone.

---

### Post by trotski on 2006-03-25
These binaries should work for Breezy, supposedly.  Just follow the instructions on this page:

[http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10](http://amarok.kde.org/amarokwiki/index.php/1.4_for_Kubuntu_5.10)

Personally, I compiled and installed the newer Taglib.  Then I did the same for libgpod.  Then I got all the necessary dev files for compiling Amarok 1.4.  I use the amarok-svn script.  I had issues with the 1.3.x series and Breezy's older Taglib.  Certain tags would cause the collection scanner to hang.  Some files even caused the whole app to crash.  These problems went away in 1.3.x when I used my own Taglib 1.4.

---

