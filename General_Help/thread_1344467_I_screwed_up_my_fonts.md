---
title: "I screwed up my fonts"
date: 2009-12-03
forum: General Help
---

### Post by majicman2005 on 2009-12-03
So I've messed around with a lot of different fonts and installed/uninstalled quite a few font packages (ubuntu 64bit 9.10).  I seem to have gotten some of the fonts back to the originals but there are still a few programs like K3b and others (especially help files) that just don't look right any more in regards to the fonts (they don't look smooth and very ugly).

How do I get everything back to default or do I need to do a reinstall of Ubuntu?

---

### Post by lidex on 2009-12-03
Try 
```
sudo apt-get install ubuntu-desktop
```

Enter that command into a terminal and press enter key.

You can find a terminal in Accessories menu. Any commands run with sudo will require your password.

---

### Post by majicman2005 on 2009-12-03
I tried the command and it didn't change anything.  I did a restart of ubuntu and it remains the same.  Any other suggestions?

Thanks for your help so far.

---

### Post by Kevbert on 2009-12-03
Another terminal command to try:
```
sudo apt-get update
sudo apt-get install -f
```
This will check for missing dependencies (hopefully that includes fonts).

---

### Post by lidex on 2009-12-03
If you are not missing any fonts any remaining issue is configuration. Also k3b is a kde app which means it uses different libraries than gnome. You can install qtconfig to help with those.
```
sudo apt-get install qtconfig-qt4
```
After fiddling with fonts it's a good idea to refresh/rebuild font cache for installed fonts to be available to programs. To do that run this command:
```
sudo fc-cache -f -v
```


**An aside here...I hadn't done anything with fonts on my system in ages so when I ran the above command to confirm it I expected nothing to happen. The terminal output showed it **adding** fonts to the cache as well as a lot of cleaning. I am a bit surprised. Next I opened ooo writer to check font usage there and it opened in about 4 seconds. OK, now I'm on the floor. Question: are these related? I have never seen openoffice move so fast.**

---

### Post by lidex on 2009-12-03
majicman2005,
I almost forgot - have you accessed the font configuration utility? You can get there by right-clicking the desktop and selecting "change desktop background". Click the "fonts" tab.

---

