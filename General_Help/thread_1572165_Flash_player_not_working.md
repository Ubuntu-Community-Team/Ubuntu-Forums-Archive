---
title: "Flash player not working"
date: 2010-09-10
forum: General Help
---

### Post by aarolilja on 2010-09-10
Flash isn't working anywhere, and haven't done so properly since I first installed Ubuntu 10.04 a month ago. I have been able to make it work for a short period of time, by doing the following:

1. clearing the cache and the cookies.
2. installing the correct plug-ins for my system.

sometimes when I do this, Flash will work for a few minutes. what can I do to resolve the problem completely?

the Flash plug-in I have is the Adobe Flash plug-in, version 10.1.82.76ubuntu0.10.04.2.

---

### Post by dirty_harry on 2010-09-10
I find the combination  of the Firefox-Addons "FLASH-AID" and "BetterPrivacy" very useful...
Flash-Aid runs a script for installing Adobe Flash and BetterPrivacy helps you to get rid of very LSO.

---

### Post by aarolilja on 2010-09-10
I already have FLASH-AID, it doesn't help. but thanks for your reply!

---

### Post by dirty_harry on 2010-09-10
some people mentioned that "hardware acceleration" caused them all the trouble.
just right-clicked on a flash element and disable it...

---

### Post by aarolilja on 2010-09-10
I'm not sure if I understand what you mean.

if I'm for example trying to watch a video on youtube, only a white box of nothing appears where the video should be, and I can't right click it.

---

### Post by ulfj on 2010-09-10
Is it just a white screen or just audio and no video?

---

### Post by aarolilja on 2010-09-10
it's just a white/empty space where the video should be.

---

### Post by sandyd on 2010-09-10
> **aarolilja said:**
> it's just a white/empty space where the video should be.
64bit or 32bit ubuntu?

---

### Post by aarolilja on 2010-09-10
64bit.

---

### Post by sandyd on 2010-09-10
> **aarolilja said:**
> 64bit.

im on my cell, but go on google and search for "flash GDK_EXPORT_WINDOWS" if your watching youtube, try switching to html5

---

### Post by aarolilja on 2010-09-11
when I google "flash GDK_EXPORT_WINDOWS" the only result is this thread.

---

### Post by desnaike on 2010-09-11
I have no idea why this happens but I experienced it years ago solved the problem by copying all the plugins in usr/lib/mozilla/plugins folder into each browsers plugin folder has worked without fail for years.

---

### Post by wojox on 2010-09-12
> **cook steel said:**
> had this problem enough times...heres how to fix. download and run this  uninstaller(select the appropriate one) ' ht tp://ww w.adobe .c om/cfu  sion/knowle dgebase /ind ex.cfm?  id=tn_14157 ' REMOVE SPACES. restart  ur pc then go an download again and install. restart again. it shud be  working now

Just out of curiosity, what's with the spaces?

---

### Post by Lukas666 on 2010-09-12
> **aarolilja said:**
> Flash isn't working anywhere, and haven't done so properly since I first installed Ubuntu 10.04 a month ago. I have been able to make it work for a short period of time, by doing the following:

1. clearing the cache and the cookies.
2. installing the correct plug-ins for my system.

sometimes when I do this, Flash will work for a few minutes. what can I do to resolve the problem completely?

the Flash plug-in I have is the Adobe Flash plug-in, version 10.1.82.76ubuntu0.10.04.2.

What do you mean by "installing"? In my case I just had to copy one file to the plugins folder. And that did it.

---

### Post by wojox on 2010-09-12
> **sandyd said:**
> im on my cell, but go on google and search for "flash GDK_EXPORT_WINDOWS" if your watching youtube, try switching to html5

I think she meant

```
GTK EXPORT WINDOWS Flash
```

---

### Post by aarolilja on 2010-09-12
> **desnaike said:**
> I have no idea why this happens but I experienced it years ago solved the problem by copying all the plugins in usr/lib/mozilla/plugins folder into each browsers plugin folder has worked without fail for years.
copying them seems a bit overkill and unmanageable with updates etc, so I made symbolic links instead. so far so good. I'll post back if it acts up.

thanks for all the help!

---

### Post by aarolilja on 2010-09-12
it did act up, still not working properly! 

googling GTK EXPORT WINDOWS Flash didn't really result in anything relevant as far as I could see.

---

### Post by desnaike on 2010-09-12
Thats why I copy them links break and if you never discover whats causing it the problem remains.

---

### Post by aarolilja on 2010-09-12
what do you mean links are breaking? when you symbolically link a directory, it is linked, and the changes that happen to the target directory happen to the links as well.

---

### Post by Ashbentiel on 2010-09-26
White box where the video should be?  Audio but no video?  It's the GTK rgba module. Here's the fix, make a script that reads:

```

#!/bin/sh
export GTK_MODULES=
/usr/bin/firefox

```

Save it as /usr/bin/fixedfox or what/wherever you prefer.  chmod a+x <scriptname>.  And then point your shortcuts to that script instead of /usr/bin/firefox.

---

### Post by Blimix on 2010-09-27
Do you have gnash installed?

I had the exact same problem:  Flash didn't work after the Ubuntu upgrade.  I tried the above suggestions, but it turned out that gnash was the problem.  (I had long ago installed gnash to fix flash problems.)  I just used Synaptic to uninstall gnash (and reinstall flashplugin-installer for good measure), and flash is playing fine now.

---

