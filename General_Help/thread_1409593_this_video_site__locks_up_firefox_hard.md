---
title: "this video site  locks up firefox hard"
date: 2010-02-17
forum: General Help
---

### Post by sdowney717 on 2010-02-17
[http://s114.photobucket.com/albums/n274/crankmy5150/?action=view&current=Jeepknocking.flv](http://s114.photobucket.com/albums/n274/crankmy5150/?action=view&current=Jeepknocking.flv)

can anyone tell me why?

It also gives a little grief to chrome.
either way I cant watch the videos on that site.

---

### Post by bluelamp999 on 2010-02-17
Locked up my Firefox too, I'm at a loss as to why though...

---

### Post by sdowney717 on 2010-02-17
I found out If you leave it, eventually it will start playing. But this is like a bug, why lock up the whole browser and other tabs because it cant play the file?

---

### Post by bluelamp999 on 2010-02-17
This is an example where Chrome's separate process per tab comes in handy!

Apparently, FF 3.7 will have something like this, where plug-ins such as Flash will be moved to computing processes that are separate from the main browser operation, protecting the latter from problems with the former

---

### Post by Satoru-san on 2010-02-17
Locked me up too, and I use no script. So it wasn't a malicious javascript code.

---

### Post by lovinglinux on 2010-02-17
Locks up here too. I have noticed that while blocking flash content, it says I need Flash 8 to view it. I don't know about compatibility of older versions of flash, but perhaps this is why it is locking.

---

### Post by dcstar on 2010-02-17
> **lovinglinux said:**
> Locks up here too. I have noticed that while blocking flash content, it says I need Flash 8 to view it. I don't know about compatibility of older versions of flash, but perhaps this is why it is locking.

It also locks up using the latest 64-bit Flash plugin (r45) from Adobe on my FF 3.0.17 system.

---

### Post by lovinglinux on 2010-02-17
> **dcstar said:**
> It also locks up using the latest 64-bit Flash plugin (r45) from Adobe on my FF 3.0.17 system.

I also use the latest 64bit flash, but on Firefox 3.6. I think the video player on that site is made for Flash 8. So perhaps this is what causing the crashes. Perhaps it is a backwards compatibility issue with the latest flash plugins.

---

### Post by Satoru-san on 2010-02-17
I have a 32 bit system.

```
satoru@localhost ~ $ emerge -pv adobe-flash

These are the packages that would be merged, in order:

Calculating dependencies... done!
[ebuild   R   ] www-plugins/adobe-flash-10.0.42.34  USE="32bit 64bit (-multilib)" 0 kB

Total: 1 package (1 reinstall), Size of downloads: 0 kB
```

latest stable flash. Yet it locks for me.

Anyone use free flash that can test it?

---

### Post by no2498 on 2010-02-17
it locked me up also
i go to a chat-cam site that uses flash an to log out i get locked up just started like a week ago if i click force every thing closes let it sit a bit  im ok
btw i hit the back button
im on 804 hardy flash 10.46 or what ever it is 2 days old

---

### Post by jamesisin on 2010-02-17
I tested this in Opera 10.10 in Ubuntu 8.10.

I surf with JS and plugins off browser-wide, so I had to enable both for this site.  (Flash requires JS to spawn the player.)

Reloading with these enabled caused a small (1.5 minute) hang (grey) of the browser.  When control returned, the player rectangle turned white (disappeared) and nothing played.

I then reloaded the page again.  The player came up and very soon went white again (no hang on this load).

---

### Post by babygenius55 on 2010-03-30
This is happening in firefox 3.7 (Minefeild) I can't even access adobe.com! What is the problem here?  3.6 won't let me chat on facebook. Opera doesn't like to use html5 video.  I really don't want a re-install Ubuntu, I think I'm going to purge all files to see what happens

---

### Post by lovinglinux on 2010-03-30
> **babygenius55 said:**
> This is happening in firefox 3.7 (Minefeild) I can't even access adobe.com! What is the problem here?  3.6 won't let me chat on facebook. Opera doesn't like to use html5 video.  I really don't want a re-install Ubuntu, I think I'm going to purge all files to see what happens

The problem described on this thread is for a particular video site, so would be better if you had created a new thread.

See [COLOR="Sienna"]**Troubleshooting**[/COLOR] section of [Firefox optimization and troubleshooting thread](http://ubuntuforums.org/showthread.php?t=1193567).

---

