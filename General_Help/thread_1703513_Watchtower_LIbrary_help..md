---
title: "Watchtower LIbrary help."
date: 2011-03-09
forum: General Help
---

### Post by Bcrowes11 on 2011-03-09
I woke up today to start the watchtower library, and when I clicked on it, I got an error message saying "The program WTLibrary.exe has encountered a serious problem and needs to close. We are sorry for the inconvenience." I updated Wine, but it's still giving that error message. I tried this iphlpapi work around, it's still not working. I'm running the latest wine version. 1.3 something, so I know it's up to date. Please help. :'(

---

### Post by cottfcfan on 2011-03-09
If the WT Library is the only thing you're running in wine.
Go into your Home folder, delete the .wine folder, then go into the .local/share/applications folder. Make sure everything in there pertains to Wine. Delete it all. This will give you a clean Wine install. Try installing the WT Library again, and it should work.
Also what Wine 1.3 version are you using 1.3.14 is the latest and WT Library works well in it.

---

### Post by colin.p on 2011-03-09
Not sure what may have happened but if you haven't already tried, try here:
[http://appdb.winehq.org/objectManager.php?sClass=version&iId=22127](http://appdb.winehq.org/objectManager.php?sClass=version&iId=22127)
as I'm quite sure one of those lads will have an idea as to how to fix it.

Should have added (posted too quick, had to go outside and get some more wood, will this winter ever end?)
I am using wine 1.3.14 and WTLB 2010 in lucid and have no issues. However, when I either update to a newer WTLB, or a new ubuntu, I always go to the winehq for a solution and the lads have never let me down yet.
You can probably count on one hand how many people have ever heard of WTLB in ubuntu forums, let alone using it. However, most wine solutions work for most win progs anyway.

---

