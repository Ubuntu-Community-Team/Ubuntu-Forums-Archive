---
title: "Firefox won't restore session"
date: 2010-12-03
forum: General Help
---

### Post by Asmodai on 2010-12-03
Hey,

recently Firefox/Minefield started to stop loading sites after some time and when exiting Firefox, the process would keep running in the background, so I have to kill it. When I did this yesterday, Firefox no longer restored my tabs from last session like usual. There's a sessionstore.bak in my profile folder whose size is 1.3 MB and seems to be intact.
Still, when renaming it to sessionstore.js, Firefox will still not load my tabs - it just displays the start page. This applies to both Firefox 3.6 and Minefield. I tried a sessionstore backup from five days ago, but the result is the same.
Is there anything else I need to do to get Firefox to restore my tabs?

Session restore in general does not seem to be broken, because when I open a few new tabs and save them, they are restored the next time I start Firefox.

---

### Post by Asmodai on 2010-12-03
Now it seems that the tabs are lost every time Minefield is killed.
Still, the original problem persists.

---

### Post by lovinglinux on 2010-12-03
Type about[noparse]:[/noparse]config in the address bar, then make sure **browser.sessionstore.resume_from_crash** and **browser.sessionstore.enabled** are set as true.

More info at [http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash](http://kb.mozillazine.org/Browser.sessionstore.resume_from_crash)

---

### Post by Asmodai on 2010-12-03
Thanks. I checked, but they were both set to true.
However, when I re-examined the sessionstore.bak file, I noticed all my tabs were in the array _closedWindows. After swapping the names windows and _closedWindows, it works fine.

---

### Post by charlestu on 2010-12-11
You can bring up the session restore window by entering:

  about:sessionrestore

in the address bar.  This will only help if you have not closed firefox since it failed to restore tabs.

Thanks to [http://www.webupd8.org/](http://www.webupd8.org/) for this tip.

---

### Post by ByRillYAN on 2012-03-20
I had this exact same problem today.  Firefox had just been updated to Firefox11 so I quit my session to let it update. I usually keep about 100-200 tabs open at a time in 5-10 tab groups.  I noticed that firefox was still running in the background so I killed it; I know this usually means that I will lose my session and have to restore from backup - no big deal.  

As usual, session didn't restore.  This time, however, when I quit firefox, backed up all sessionstore files, renamed sessionstore.bak to sessionstore.js, and opened firefox all I got was my homepage.  After a bit of messing around with editing the files to no avail, I googled a bit a found this thread.  Three more minutes editing the files and I got my firefox session back!







For anyone stumbling on this in the future, here's what I did:

1) After locating the file that I wanted to use (I assume you already know how to do that if your reading this thread), I opened it in a text editor [gedit works just fine, in win7 there is an edit option in the context menu].

2) Look at the very begging of the file, if you see this same thing, then you have the same problem:

{"windows":[],"selectedWindow":0,"_closedWindows":[{"tabs":[{"entries":[{"url":

It should be followed by a long string of urls in separate quotes. Those are the urls you want to restore.


3) change "selectedWindow":0," to "selectedWindow":1,"



4)copy everything between  


"_closedWindows":[     


and      


,"session":{"state":"running","lastUpdate":1332230338220,"startTime":1331123353813,"recentCrashes":0},"scratchpads":[]}

*note* the numbers in there will be different, don't worry about that.*note*




5) Paste what you copied between the brackets in 


{"windows":[*paste here*]


6) Save the file as sessionstore.js in the proper folder and start firefox, you should have your lost session back. finally.

---

### Post by GeoAndy on 2012-12-07
^Thanks for this post--it helped my recover a corrupt sessionrestore file (twice)

---

