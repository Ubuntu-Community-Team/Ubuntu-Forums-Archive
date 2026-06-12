---
title: "Terminal Issues"
date: 2011-04-05
forum: General Help
---

### Post by Kyzyks9001 on 2011-04-05
Okay, I'm trying to install iTunes onto ubuntu, i already got wine and configured it and i type in "wine iTunesSetup.exe" and then it says wine: cannot find L"C:\\windows\\system32\\iTunesSetup.exe".

Any ideas?

---

### Post by ajgreeny on 2011-04-05
You must be in the same folder as the .exe file when you use that command, so if it is on your desktop use ```
cd Desktop && wine iTunesSetup.exe
```

I have never used iTunes and don't know how well it works in wine either, so you may be wasting your time, but the general info here will perhaps give you a chance to try.

---

### Post by seawolf167 on 2011-04-05
[Here ]("http://appdb.winehq.org/objectManager.php?sClass=application&iId=1347")is the WineDB for iTunes. Find your version number, click it, then scroll down for installation instructions and a list of what works and what doesn't.

---

