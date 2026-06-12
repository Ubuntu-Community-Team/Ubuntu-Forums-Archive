---
title: "Hidden cache folder in home folder - safe to delete?"
date: 2011-06-08
forum: General Help
---

### Post by kanishkdudeja on 2011-06-08
upon browsing the home folder in my ubuntu system, i came across a hidden cache folder..

it occupied around 700 mb of space..and im falling short of space..

can i delete the contents in the folder? are they safe to delete?

---

### Post by Jouke74 on 2011-06-08
First check what is in the cache folder?

Then check this to clean Ubuntu (careful with this one):
[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

---

### Post by SoFl W on 2011-06-08
Please tell us the name of the hidden folder in question.
What I always do with files or folders I am unsure of is rename them "foldername" to "foldername_ORIG", and then try working with the system a few days.  If you needed the file/folder it is easy to fix.

When is the last time you emptied the trash folder?

---

### Post by kanishkdudeja on 2011-06-08
just emptied the trash some time back..

the folder is named .cache..

there are lots of folders under this folder..
```

banshee-1
chromium
compizconfig-1
dconf
desktop-couch
event-sound-cache.tdb.d50f48b73b25fed978ad7cf100000009.i686-pc-linux-gnu
evolution
gmailwatcher
google-chrome
gwibber
indicators
media-art
notify-osd.log
pitivi
rhythmbox
software-center
sso
totem
transmission
ubuntuone
unity
update-manager-core
usb-creator.log
wallpaper
zeitgeist

```

for example - when i open the chromium folder..i get to see saved vids of recent youtube videos ive watched..

and some pics of webpages i open too often.

---

### Post by Jouke74 on 2011-06-08
Ok, then it is the general cache folder. 

You can empty that, but as soon as you start using the web again 
etc. it will quickly refill. 

Also I am a bit worried about e.g. the Zeitgeist folders, which likely contains your document history and evolution, Gwibber etc.

I suggest you leave it alone.

---

### Post by kanishkdudeja on 2011-06-09
okay..i just deleted the data in the chromium and the gooogle-chrome folder..which contained all the cache for the browsers.

670 mb of 700 mb has been freed..so almost all of the memory was taken up the brower's cache..

so that means

remaining folders take about 30 mb..

so thats okay..

thanks guys..:)

---

