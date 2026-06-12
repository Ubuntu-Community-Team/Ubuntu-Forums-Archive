---
title: "Google Chrome doesn't show up"
date: 2012-07-03
forum: General Help
---

### Post by Anarchj on 2012-07-03
I'm not able to view Google Chrome window anymore after upgrading to 20.0.1132.47-r144678, anyway I can see "chrome" and "google-chrome" processes in System Monitor after launching the application from the Dash.
I'm in Ubuntu 12.04 and I'm using Unity-2D

---

### Post by Anarchj on 2012-07-03
up!

---

### Post by Anarchj on 2012-07-03
Ok, seems to be a bug in built-in Flash of the lastest version.
Workaround: > google-chrome --disable-bundled-ppapi-flash
Here's the discussion
[http://code.google.com/p/chromium/issues/detail?can=2&start=0&num=100&q=&colspec=ID%20Pri%20Mstone%20ReleaseBlock%20Area%20Feature%20Status%20Owner%20Summary&groupby=&sort=&id=134940](http://code.google.com/p/chromium/issues/detail?can=2&start=0&num=100&q=&colspec=ID%20Pri%20Mstone%20ReleaseBlock%20Area%20Feature%20Status%20Owner%20Summary&groupby=&sort=&id=134940)

---

### Post by Rexilion on 2012-07-07
Thanks for the suggestion, worked like a charm. I placed the suffix you suggested in ~/.local/share/applications/google-chrome.desktop (which I copied from /usr/share/applications).

Too bad the malfunctioning piece is the only reason I installed this browser on my parents computer ](*,)

P.S. I ran into this issue too with the 'vanilla Flash' version. The 'root' bug is [here]("https://bugbase.adobe.com/index.cfm?event=bug&id=3161034"). Seems like Adobe is compiling flash with SSE2 SIMD-instructions which this 9 year old computer does not support. I dug into the Adobe archives and the latest version that functions is referenced as:

/home/gebruiker/.mozilla/plugins/libflashplayer-11.1r102.63.so (which is better than the alternative that people suggest, i.e. resort to version 10 (wth..))

](*,) ](*,) ](*,)

---

