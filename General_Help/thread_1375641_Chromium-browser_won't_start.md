---
title: "Chromium-browser won't start"
date: 2010-01-08
forum: General Help
---

### Post by polki@mac.com on 2010-01-08
Update-notifier told me there were updates today and I installed them. Among them were some for chromium (the browser, not the game :) ). After the update I couldn't start the browser. I tried starting from terminal and got:

"Inconsistency detected by ld.so: dl-minimal.c: 138: realloc: Assertion `ptr == alloc_last_block' failed!"

"I haz a fail!", I thought to myself and then tried rebooting and then reinstalling. Neither worked.

This is on a 64-bit machine. Everything else works as expected. Using Firefox now, but I want my chromium-browser as well.

Any ideas?

---

### Post by jimendeath on 2010-01-08
Hi,

I got the same error after updating some things (i cannot remember which ones) i been notified by ubuntu system updater.

I'm running Ubuntu 9.10 - Karmic Koala

Thanx in advance

---

### Post by d-E-a-D on 2010-01-08
same here

---

### Post by exutable on 2010-01-08
yep me too, right after an update

Have 9.10 64 bit

---

### Post by aninona on 2010-01-08
same here kk 32

---

### Post by pepitux on 2010-01-08
Me too, since it's updated this morning :(

I have Karmic 64

---

### Post by mkvnmtr on 2010-01-08
We are using a daily build. Sometimes it does not work or has bugs. Probably the next update will fix it. To not have this problem sometimes you can comment out the repositories when you have a build working well or you could download the Google version.

---

### Post by garg on 2010-01-08
Same problem here. Latest build 4.0.293.0~svn20100108r35769-0ubuntu1~ucd1~karmic       Chromium browser
does not launch.

I reverted to the old version. Check if your apt cache has the old version:

```
ls -lrt /var/cache/apt/archives/chromium-browser
```

I had 

```
-rw-r--r-- 1 root root 10192464 2010-01-03 23:26 /var/cache/apt/archives/chromium-browser_4.0.289.0~svn20100104r35448-0ubuntu1~ucd1~karmic_i386.deb
-rw-r--r-- 1 root root   463090 2010-01-06 03:37 /var/cache/apt/archives/chromium-browser-inspector_4.0.291.0~svn20100106r35606-0ubuntu1~ucd1~karmic_all.deb
-rw-r--r-- 1 root root 10205836 2010-01-06 03:37 /var/cache/apt/archives/chromium-browser_4.0.291.0~svn20100106r35606-0ubuntu1~ucd1~karmic_i386.deb
-rw-r--r-- 1 root root   470546 2010-01-07 23:28 /var/cache/apt/archives/chromium-browser-inspector_4.0.293.0~svn20100108r35769-0ubuntu1~ucd1~karmic_all.deb
-rw-r--r-- 1 root root 10237162 2010-01-07 23:28 /var/cache/apt/archives/chromium-browser_4.0.293.0~svn20100108r35769-0ubuntu1~ucd1~karmic_i386.deb
```

293 stopped working, so I tried to install 291 using:

```
sudo dpkg -i /var/cache/apt/archives/chromium-browser_4.0.291.0~svn20100106r35606-0ubuntu1~ucd1~karmic_i386.deb
```

and 

```
sudo dpkg -i /var/cache/apt/archives/chromium-browser-inspector_4.0.291.0~svn20100106r35606-0ubuntu1~ucd1~karmic_all.deb
```

And now it is running. Don't install updates I guess until build 295?

---

### Post by garg on 2010-01-08
Here is the bug report:
[http://code.google.com/p/chromium/issues/detail?id=31809&sort=-id&colspec=ID%20Stars%20Pri%20Area%20Type%20Status%20Summary%20Modified%20Owner%20Mstone%20OS](http://code.google.com/p/chromium/issues/detail?id=31809&sort=-id&colspec=ID%20Stars%20Pri%20Area%20Type%20Status%20Summary%20Modified%20Owner%20Mstone%20OS)

The fix that they suggest is:

> In the meantime, you can downgrade to yesterday's version, or shift to one of the 
other channels/PPAs:

[https://launchpad.net/~chromium-daily/+archive/dev](https://launchpad.net/~chromium-daily/+archive/dev)
[https://launchpad.net/~chromium-daily/+archive/beta](https://launchpad.net/~chromium-daily/+archive/beta)

and

> 1. System > Administration > Software Sources
2. Click 'Other Software'
3. Choose chromium deps and change them to read:
[http://ppa.launchpad.net/chromium-daily/dev/ubuntu](http://ppa.launchpad.net/chromium-daily/dev/ubuntu) instead of 
[http://ppa.launchpad.net/chromium-daily/ppa/ubuntu](http://ppa.launchpad.net/chromium-daily/ppa/ubuntu)
**You should have 2 of them, one for sources and the other ;)

Close and choose reload when prompted.

Goto Synaptic and type chromium in the search.. when chromium-browser is displayed 
highlight and then from the menubar choose 'Packages > Force version' and you should 
get a drop down.. just choose the previous version from the list and away you go ;)

---

### Post by rburkartjo on 2010-01-08
i experienced the same problem. will just wait until the next update. for a while i thought was just on my end

---

### Post by rburkartjo on 2010-01-09
as of latest update, i installed 5:30am cdst, chromium is up and running. firefox seems so slow after using chromium and have more extensions installed in chromium than ff

---

### Post by pepitux on 2010-01-09
fixed after update ;)

---

### Post by Muskegman on 2010-01-09
have the same problem here also. I downloaded chromium a week ago and it started and ran fine. 2 days ago i got the latest updates for chromium via update manager and tried starting it up..... nothing , it wont start up now. 

For now i have removed chromium and will stick with firefox.

---

