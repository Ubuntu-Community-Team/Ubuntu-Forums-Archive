---
title: "missing firefox icon"
date: 2012-01-30
forum: General Help
---

### Post by DwalerXIII on 2012-01-30
After a fresh install of ubuntu 11.10 I have a blanc icon in place of the firefox icon but firefox starts when clicking on it. When typing firefox in the searchbox of the app-lens, firefox is not found.

This is not a great issue as long as I can start firefox with the blank icon.

The problem is however that when I click a link in an external program, firefox always starts a new window and goes to the startpage, not to the requested page.

---

### Post by kcirrab on 2012-01-30
try the following in terminal

 sudo apt-get remove firefox

sudo apt-get firefox

Report back any problems

---

### Post by DwalerXIII on 2012-01-30
Hi kcirrab,

that didn't work. I tried it already with packetmanager.

---

### Post by raja.genupula on 2012-01-30
do this 

```
unity --reset
unity --reset-icons
```

hope that helps .

All the best.

---

### Post by DwalerXIII on 2012-01-31
All my icons were reset but the firefox icon stays blank.
Maybe it has something to do with the fact that firefox can not be found when searching for applications.

---

### Post by raja.genupula on 2012-01-31
**sudo apt-get install --reinstall firefox **

and give a restart  , if things not fine even , then do this . 

[B]sudo apt-get remove --purge firefox
&
sudo apt-get install firefox

[/B]hmm let us know what you got . 
All the best man .:):)

---

### Post by winh8r on 2012-02-07
Hi,
I had a similar issue a while back , but cannot remember where I wrote down how i fixed it!!!

Firstly, this file:

/usr/share/applications/desktop.en_GB.utf8.cache 

(yours might be a little differentif you are not using the en lang pack)

Search for the firefox entry and make sure that it says "icon=firefox"

Then

Check to see if there is a firefox icon in /usr/lib/firefox-10.0/icons

Also check to see if there is a link to the above location in

/usr/share/pixmaps/


You can get a new icon from here:

[http://blog.mozilla.com/faaborg/2009/06/18/the-new-firefox-icon/]("http://blog.mozilla.com/faaborg/2009/06/18/the-new-firefox-icon/")

I cannot remember how I made the link between /pixmaps and the /usr/lib
directories.

But i am sure there will be someone who can help you from here, if I recall correctly it was something to do with a firefox update which caused the old link to become obsolete due to version numbering or size or something.

Anyway , hope this gets you somewhere.

I will keep looking for my written instructions and will post here if I find them.




***EDIT***  found this thread which will direct you to the problem quickly as it is for 11.10 with Unity

[http://ubuntuforums.org/showthread.php?t=1877070]("http://ubuntuforums.org/showthread.php?t=1877070")


(still looking for that old book with my old "fixes" in it though!!!)

---

