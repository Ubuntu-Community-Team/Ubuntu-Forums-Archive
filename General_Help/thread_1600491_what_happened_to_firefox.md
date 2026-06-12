---
title: "what happened to firefox?"
date: 2010-10-19
forum: General Help
---

### Post by nick3501 on 2010-10-19
ok not sure if it was an update or what, but none of my RSS feeds seem to load, i also have a folder in my toolbar that normally had a dropdown menu to about 6 or 7 different sites i visited frequently, and when iclick it nothing happens (no drop down tab stays 'clicked in')...if i try and hit 'reload live bookmarks' i get a big fancy error message that wont go away and i have to force quit firefox, sometimes firefox refuses to close when i click the X.  I have went into synaptec and completly removed anything firefox and firefox related, restarted, re-installed and same problem!  I have the standard BBC RSS feed as well as 4 others, only one works but not well (only has one news story sometimes 2...there should be at least 15 in the list)  is there a way i can completley wipe firefox leaving no trace of it on my computer?  because i cant even delete most RSS tabs either.  Chromium works fine in the meantime:)

---

### Post by lovinglinux on 2010-10-19
Possibly a database corruption. Close Firefox, go to your Firefox profile folder (i.e. ~/.mozilla/firefox/<profilename>) and move the file places.sqlite to a safe place outside the profile folder. Start Firefox and restore a bookmark backup. To do that, open “Bookmarks >> Organize Bookmarks” then select one of the options of the “Import and Backup” drop-down menu. There should be some backups there, that are created automatically.

---

### Post by nick3501 on 2010-10-19
thanks for the help...but places.sqlite doesnt seem to exist on my computer...not sure exactly where it would be but a filesystem search doesn't show it.  i have all my bookmarks in chromium so i can just import them back into firefox...should i just searchand delete any folder/file named mozilla or firefox? then re-install?

edit: heres the error im getting with rss feeds and dropdown folders:



ASSERT: node must have _DOMElement set
Stack Trace: 
0:TV_V_nodeRemoved([object ResultNodeClassInfo],[object ResultNodeClassInfo],7)
1:removeFolder(204462)
2:LS_deleteLivemarkChildren(204462)
3:LLL_runBatched([xpconnect wrapped nsIFeedResult])
4:runInBatchMode([object Object],[xpconnect wrapped nsIFeedResult])
5:LLL_handleResult([xpconnect wrapped nsIFeedResult])
6:handleResult([xpconnect wrapped nsIFeedResult])
7:FP_sendResult()
8:FP_endDocument()
9:onStopRequest([xpconnect wrapped (nsISupports, nsIRequest, nsIChannel)],null,0)
10:FP_onStopRequest([xpconnect wrapped (nsISupports, nsIRequest, nsIChannel)],null,0)
11:onStopRequest([xpconnect wrapped (nsISupports, nsIChannel, nsIHttpChannel, nsIRequest)],null,0)
12:LLL_onStopRequest([xpconnect wrapped (nsISupports, nsIChannel, nsIHttpChannel, nsIRequest)],null,0)

---

### Post by lovinglinux on 2010-10-19
Go to your **/home/username/** folder, then hit CTRL+H to display hidden files, then open the folder **.mozilla**, then the folder **firefox**, then your default profile folder. The file **places.sqlite** must be there.

For more info about profiles, see [http://firefox-tutorials.blogspot.com/2010/05/profiles.html](http://firefox-tutorials.blogspot.com/2010/05/profiles.html)

---

### Post by nick3501 on 2010-10-19
:guitar: worked like a charm...thanks!

---

