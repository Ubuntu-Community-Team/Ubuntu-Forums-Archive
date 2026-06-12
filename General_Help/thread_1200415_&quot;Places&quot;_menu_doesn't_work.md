---
title: "&quot;Places&quot; menu doesn't work"
date: 2009-06-30
forum: General Help
---

### Post by fboxall on 2009-06-30
My ubuntu 9.4 has worked well up to now.  But now I cannot get to most of the locations in the "places" menu.  For example when I click on "desktop", my mouse pointer arrow turns to busy indicator for about 10 seconds, then back to arrow, but my desktop doesn't appear. Same for "home folder", "documents", "music", "computer", etc.  However on "search for files" I can find and open files that I know are on the desk top which I cannot get to.  I have tried switching desktops - that doesn't help.  Other computer functions are working normally, e.g. Thunderbird mail client, firefox browser, music player.  Please help me.

---

### Post by dmizer on 2009-06-30
What is the output of:
```
ls -la ~/Desktop
```

---

### Post by fboxall on 2009-06-30
the output is: ls: cannot access /home/frank/desktop: no such file or directory

---

### Post by dmizer on 2009-06-30
> **fboxall said:**
> the output is: ls: cannot access /home/frank/desktop: no such file or directory

Not **[COLOR="Red"]d[/COLOR]**esktop, **[COLOR="Red"]D[/COLOR]**esktop. Linux is case sensitive. ;)

---

### Post by prshah on 2009-06-30
> **fboxall said:**
> 
But now I cannot get to most of the locations in the "places" menu.

There was a small bug similar to this a while back; try [this solution]("http://ubuntuforums.org/showpost.php?p=6082327&postcount=2") and see if it helps.

---

### Post by fboxall on 2009-06-30
Thanks to dmizer and prshah for their responses.  I have managed to solve my problem by restarting in recovery mode.  I should have tried that earlier.  Owning a computer is a continual learning experience.  fboxall

---

