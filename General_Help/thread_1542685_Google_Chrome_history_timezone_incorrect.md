---
title: "Google Chrome history timezone incorrect"
date: 2010-07-30
forum: General Help
---

### Post by raf-kig on 2010-07-30
I'm in the PDT timezone and my Ubuntu time setting is correct. However my Google Chrome history shows times that are one hour earlier. It's almost as if it doesn't recognize daylight saving time. If I type

```
javascript:new%20Date().toString()
```in the address bar it displays the correct time. Is anyone else having this issue with Google Chrome 5.0.375.125?

---

### Post by raf-kig on 2010-07-31
Bump. It works properly with the Windows version. I tried clearing all history, everything, and the history times are still one hour behind.

---

### Post by raf-kig on 2010-07-31
Bump. I completely removed Google Chrome and reinstalled the "stable" release — 5.0.375.125, and still no change. This is driving me crazy. I'm obsessing over it!

---

### Post by cariboo on 2010-07-31
Please don't bump your thread more than once every 24 hours. Excessive bumping makes it look like you are actually getting help with your problem, so the person that may be able to answer your question may pass it by.

---

### Post by holadebob on 2010-07-31
I had the same problem, ie Chromium history times, and I went through my system looking for remaining files after uninstalling Chromium, thought I had them all, but there are many that are sharing with Firefox, etc and I guess that was where the problem was?, and a reinstall of Chromium didn't catch the problem, so what I actually ending up doing is doing a complete from scratch reinstall of 10.04. 
To this day I have no idea what caused the glitch in Chromium and haven't had it since, so knock on wood.

Terrible solution I know, but I had no help trying to find the problem either.

Bob

---

### Post by raf-kig on 2010-07-31
Thanks Bob. I don't know if I'll take such a drastic step as reloading Ubuntu. Funny thing is I'm somewhat convinced that it's all related to daylight saving time because last night at midnight it changed the date to the proper date, but continued to show times as one hour earlier. Oh well, maybe when we go back to standard time it'll right itself. Thanks again for your response.

---

### Post by TNT1 on 2010-07-31
I just noticed all the files I have downloaded with chromium have the incorrect time stamp. Is this the same issue?

---

### Post by raf-kig on 2010-07-31
I don't think it's related. My file downloads show the correct time.

---

### Post by Bukoptimistas on 2010-08-01
Well i am having this problem too. 
Also all my Chrome bookmarks icons (favicons) disspeared, changed to default white. But favicons corectly shown in tabs. Anyone has that strange behaviour?
Maybe faulty new Chrome version?

---

### Post by raf-kig on 2010-08-01
> **Bukoptimistas said:**
> Well i am having this problem too. 
Also all my Chrome bookmarks icons (favicons) disspeared, changed to default white. But favicons corectly shown in tabs. Anyone has that strange behaviour?
Maybe faulty new Chrome version?

Yes, I just now noticed that same behavior.

---

### Post by Bukoptimistas on 2010-08-04
White bookmarks icons (favicons) problem solved by deleting facebook default profile folder. (~/.config/google-chrome/default). Used lastpass extension and google bookmark sync to import all passwords and bookmarks. When you delete profile folder, you lose all your saved information (history, pass, forms, bookmarks, etc). 
When you again run Chrome browser default folder is created with default settings. 

**NB. Good idea to make backup of default folder.**

Anyhow this not corrected history time. its -1 hour.

---

### Post by raf-kig on 2010-09-02
With the latest update, 6.0.472.53, Google Chrome now reports the correct time in History.

---

