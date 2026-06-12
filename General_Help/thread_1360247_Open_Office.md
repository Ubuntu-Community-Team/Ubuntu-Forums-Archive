---
title: "Open Office"
date: 2009-12-20
forum: General Help
---

### Post by cmcanulty on 2009-12-20
Lately every time I boot up it opens to a new office document instead of my desktop. How can I fix this? I don't have a document open when I shut down.

---

### Post by FearfulJesuit on 2009-12-20
Can you go to Preferences -> Startup Applications and see whether or not you have open office listed in there to start when Ubuntu starts? If so, go ahead and remove it. That should fix the problem.

---

### Post by cmcanulty on 2009-12-20
It's not even on that list

---

### Post by FearfulJesuit on 2009-12-20
That's interesting C-Mac. I couldn't find anything in OOO options that would allow you to start it when Ubuntu starts. My solutions to these are always kind of extreme so all I can suggest at this point is do a complete re-install of OOO. Go to synaptic do a complete removal of the packages and re-install them. This generally removes configuration files that might be causing it to open on startup. If OOO still opens up a blank document on startup then you know it's the config in ubuntu that's the culprit. Hopefully, somebody else can step in and help you locate and edit the conf file that is the culprit. 

My thought process is that the removal/install will atleast act as a diagnostic tool and at worst you only lose custom configs for OOO that you've created.

---

### Post by corncob on 2009-12-20
I can't find the post at the moment but my problem with OOO was that the menu fonts where white against a white background and I had to guess what they were or highlight them.  Somebody suggested that I change my theme because "OOO doesn't play well with some themes".  Accordingly, I downloaded and installed a new theme and, presto, the menu font was black as it should be.

---

### Post by scouser73 on 2009-12-20
The only thing I can think of would be to delete your **.openoffice.org** folder in **/home/username** and restart OpenOffice again, thus creating a new profile and seeing if you still encounter the same problem.

---

### Post by corncob on 2009-12-20
> **cmcanulty said:**
> It's not even on that list

Try opening ~.config/autostart and see if there is any reference there that can be removed.

---

### Post by cmcanulty on 2009-12-21
It isn't in autostart I reinstalled writer and will see if that works.

---

### Post by cmcanulty on 2009-12-21
Reinstaaling writer fixed it thanks everyone

---

