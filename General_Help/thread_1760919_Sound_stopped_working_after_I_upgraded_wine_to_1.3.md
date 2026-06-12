---
title: "Sound stopped working after I upgraded wine to 1.3.20"
date: 2011-05-17
forum: General Help
---

### Post by 3 frags left on 2011-05-17
Well, let's say I was really curious and ended up upgrading my wine version to 1.3.20 before it was released to the PPA repos. I downloaded it via git, compiled & installed, but now it did not detect my drivers anymore. It even warned me when i ./configure'd it, but I didn't listen. I tried, also, remove purge all wine packages I own and reinstall them from Ubuntu, but the dud 1.3.20 version is still installed. Is there a way to bring the sound back? Or, is there a way to revert this installation and make me able to install 1.3.19 back?

The following message appears when I access the "Audio" tab @ winecfg:
```
Found driver in registry that is not available ! 
Remove 'alsa' from registry?
```

Any help? Puh-leeeeeze?

---

### Post by 3 frags left on 2011-05-17
Also, here is the result of typing *dpkg -l | grep wine*
```
dpkg -l | grep wine
ii  ttf-symbol-replacement-wine1.3                1.3.19-0ubuntu1~maverick1~ppa1                                   Free font with the same metrics as Symbol
ii  wine1.3                                       1.3.19-0ubuntu1~maverick1~ppa1                                   Microsoft Windows Compatibility Layer (Binary Emulator and Library)
ii  wine1.3-gecko                                 1.2.0-0ubuntu1~maverickppa1                                      Microsoft Windows Compatibility Layer (Web Browser)
ii  winetricks                                    0.0+20110429~ppa1                                                Microsoft Windows Compatibility Layer (winetricks)
```
And yet when I type *wine --version*...
```
wine-1.3.20-44-gddad22d
```
That's awfully confusing.

---

### Post by gsmanners on 2011-05-17
You need to remove the source version from wherever you compiled it. Apt doesn't just magically know everything you're using in /usr/local or where you installed stuff.

```
cd /where/you/compiled/wine/
sudo make uninstall
```

see: [http://www.winehq.org/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE](http://www.winehq.org/docs/wineusr-guide/installing-wine-source#UNINSTALLING-WINE-SOURCE)

---

### Post by 3 frags left on 2011-05-17
Thank you sir, that did the trick! That was a silly mistake I did... :tongue: Marking the thread as solved.

---

