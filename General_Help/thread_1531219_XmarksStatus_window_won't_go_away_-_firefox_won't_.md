---
title: "Xmarks:Status window won't go away - firefox won't start"
date: 2010-07-14
forum: General Help
---

### Post by zcacogp on 2010-07-14
Chaps, 

I'm not sure whether this should be in the 'Beginner' section, 'cos I'm still finding my way a little with Ubuntu, but here goes ... 

On my laptop, whenever I try to start Firefox I am told there are updates available (to Adblock Plus). I click "Install Updates", it downloads them and installs them, then opens a window called "Xmarks:status", with a progress bar moving (briskly) from left to right. This says the following: 

Bookmarks          (ready)
Passwords          (ready)
Open Tabs          (ready)

... and has a "Cancel" button. 

And this window never goes away, and thus the Firefox window never appears. (The progress bar still moves briskly, but nothing further happens.)

If I click the "Cancel" button the window doesn't go away. If I kill the Firefox process then it disappears, and I can re-start it if I choose to but it just hangs again at the same point. 

I have re-booted the computer and the same thing happens. 

While it is 'hung', the CPU activity goes up to about 30%. It drops back down when I kill the Firefox process. 

I have tried starting Firefox using 'firefox' from a terminal, but there is no more information reported. 

What should I do? 

(The laptop is an IBM X31s, running 10.04 Jaunty. It's up to date. It has an internet connection, which works fine - I can use it to download updates.) 

All ideas welcomed - thanks. 


Oli.

---

### Post by sgosnell on 2010-07-14
Try uninstalling, or at least disabling, xmarks and see what happens.  Are you sure you have the correct username and password in xmarks, and a good internet connection?  I haven't seen that problem with xmarks, so it's hard to diagnose.

---

### Post by TechBeastie on 2010-07-14
You could also try disabling Xmark's "synch at shutdown" feature (assuming you can get into Firefox at all).  And if worst comes to worst, you can always create an entirely new firefox profile (run firefox -ProfileManager), and then manually copy places.sqlite and any other useful configuration files into the new profile from the old.

---

### Post by WorMzy on 2010-07-14
I'd open Fx in safemode (Alt+F2, and run 'firefox -safe-mode'), disable Foxmarks, restart Fx and see if it makes any difference. I have Xmarks installed in my cross-platform Fx profile, and I've never had any problems with it on either Windows or Linux; perhaps you got a corrupted installation though, so try reinstalling it.

---

### Post by lovinglinux on 2010-07-14
> **WorMzy said:**
> I'd open Fx in safemode (Alt+F2, and run 'firefox -safe-mode'), disable Foxmarks, restart Fx and see if it makes any difference. I have Xmarks installed in my cross-platform Fx profile, and I've never had any problems with it on either Windows or Linux; perhaps you got a corrupted installation though, so try reinstalling it.

+1

To start Firefox in safe mode use this:

```
firefox -safe-mode
```

I'm not a big fan of Xmarks because of performance issues like that. Seems to me Firefox is taking too long to process the data merging.

Keep in mind Firefox 4 will come with a built-in sync feature, that can sync bookmarks, passwords, history, tabs and preferences. If you wanna try it now, you can install [Firefox Sync](https://addons.mozilla.org/en-US/firefox/addon/10868/).

---

### Post by zcacogp on 2010-07-15
Chaps, 

Thanks for your answers. Lots to have a go with, and I'll keep you posted. I don't have the machine with me at the mo but will have a go this evening. 

Thanks for your input. 


Oli. 

P.S. Firefox 4? Sounds very interesting. May just have to try that ... thanks LL!

---

### Post by sgosnell on 2010-07-15
The reviews on Firefox Sync aren't good.  I haven't tried it, but every review on the download page is very negative, saying it doesn't work and loses bookmarks.  I think I'll stick with XMarks, at least for the time being.

---

### Post by lovinglinux on 2010-07-15
> **sgosnell said:**
> The reviews on Firefox Sync aren't good.  I haven't tried it, but every review on the download page is very negative, saying it doesn't work and loses bookmarks.  I think I'll stick with XMarks, at least for the time being.

Wow. Thanks for the alert. I haven't visited the extension site since the release of version 1.4 and only saw all those bad reviews now. Pretty scary. It used to work pretty well before that version. 
Although it seems to be working here, I will disable it for now.

---

### Post by zcacogp on 2010-07-15
Chaps, 

Back to the original topic - removing and re-installing Xmarks seems to have cured the problem. Thanks. Getting into firefox using firefox -safe-mode was the key. 

Thanks for your help. 


Oli.

---

