---
title: "FTP links incorrectly open in Chrome...sometimes"
date: 2011-06-10
forum: General Help
---

### Post by scorchgeek on 2011-06-10
I'm trying to set up this system (new Ubuntu 11.04 system) so that I can access FTP through Nautilus. So I used Places --> Connect to Server (using classic GUI), filled everything out right and bookmarked it, and when I click on the bookmark from the Places menu...Google Chrome opens it. On the other hand, if I already have Nautilus open and click the bookmark on the left side of the screen, it correctly switches the contents of the window to that location--so the bookmark is set up right. I suppose I could just not open it from the Places menu, but that seems needlessly annoying.

So is there some reason that the new version likes to open it in Chrome, or is it my Chrome settings? If the latter, I can't find an "Open FTP Links" option or so in the settings anywhere. In any case, on 10.10 it worked just fine, and I also had Chrome installed then. Any help would be very much appreciated.

---

### Post by ryanomara on 2011-07-01
I have the same problem.

---

### Post by rotten777 on 2011-08-21
> **ryanomara said:**
> I have the same problem.

me too. still awaiting a proper fix.

---

### Post by Wim Sturkenboom on 2011-08-21
Did you check launchpad if the bug has been reported? If not, why don't you submit a bug report? If developers are not aware of a problem, it will never be fixed.

---

### Post by orathaic on 2011-12-15
i finally came across a fix for this.
```

from terminal:
gksu gedit /usr/share/applications/defaults.list

find:
x-scheme-handler/http=firefox.desktop;google-chrome.desktop
x-scheme-handler/https=firefox.desktop;google-chrome.desktop
x-scheme-handler/ftp=nautilus-folder-handler.desktop

```

change the line for ftp handling to nautilus.

hope that helps!

---

