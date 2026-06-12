---
title: "Firefox and flash player"
date: 2009-08-26
forum: General Help
---

### Post by whalescreams on 2009-08-26
I just installed Kubuntu and I cant seem to Install firefox after I download it.. same with the flashplayer that i need... I installed that but still doesnt work.. any tips or ideas

---

### Post by credobyte on 2009-08-26
Did you installed them from repos ?

```
sudo apt-get install firefox flashplugin-nonfree
```

---

### Post by whalescreams on 2009-08-26
I have no idea what repos is.....

I installed firefox from mozilla website... and the flashplayer from adobe (or should i say tried to install it

---

### Post by credobyte on 2009-08-26
> **whalescreams said:**
> I have no idea what repos is.....

I installed firefox from mozilla website... and the flashplayer from adobe (or should i say tried to install it

[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) - this should give you some basics of what repositories ( repos :p ) are and what methods of installing software you *should* prefer.

---

### Post by whalescreams on 2009-08-26
so I originally started with ubuntu and now have switched to kubuntu..... 
 
fishing through stuff i think i may have found the add/remove under applications/system/software management... the kp package kit... I got firefox installed... but it does not find anything for the adobe flash player

---

### Post by whalescreams on 2009-08-26
and i have installed the sudo apt-get install firefox flashplugin-nonfree............
 
Still nothing... Im trying to go on youtube and maybe find some tutorials to watch, but i cant watch any videos yet

---

### Post by Yvan300 on 2009-08-26
Ok, did you get firefox working, if so then try installing the deb file for flash that is available on the adobe site. [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/)

---

### Post by Dullstar on 2009-08-26
Could it just be that Adobe Flash Player for Linux was made by a two year old?

At least, it feels like it! :lolflag:

---

### Post by HuaiDan on 2009-08-28
Make sure you unhide hidden files in your file browser (probably nautilus) (edit/preferences/show hidden and backup files). Go to your home folder. Find .mozilla  (the "." in front means it's a hidden folder). If there's not a folder therein called plugins, create one called "plugins", without the quotes.  Find an appropriate 32 or 64bit version of libflashplayer.so  online somewhere. Google search it, you'll find it from a reliable source.  Unzip it to your new plugins folder. Restart firefox.

So you should have something like
/home/**your username**/.mozilla/plugins/libflashplayer.so

---

### Post by whalescreams on 2009-08-28
got it all figured out... found a flash player through the kp package kit that actually worked this time

---

