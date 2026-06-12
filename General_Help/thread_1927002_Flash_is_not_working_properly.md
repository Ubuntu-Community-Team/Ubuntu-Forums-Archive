---
title: "Flash is not working properly"
date: 2012-02-17
forum: General Help
---

### Post by sedan374 on 2012-02-17
So recently (I believe it was on Tuesday or yesterday) my flash started acting strange after I installed some new updates. YouTube still works (though it's always on HD mode and sometimes the video player is smaller than it was before) but other things that require flash do not. The flash games I play instructs me to install flash again. When I try to stream videos from other sites it never loads. I uninstalled and then installed and adobe flash through the software system and tried sudo-get through the terminal but no avail.

---

### Post by euthyfro on 2012-02-17
the exact same thing is happening to me, flash was fine earlier this week then i got the update & everything went to hell.  I tried re-installing as well to no avail, went to the adobe site & saw the install latest version options.  it has APT for Ubuntu 10.04+ listed; should i try this & if so what should i use to open it when asked?

---

### Post by sedan374 on 2012-02-17
The Adobe flash which I have installed, I got it through the Ubuntu Software Centre.

---

### Post by SixalivE on 2012-02-18
Same problem here. I eventually reinstalled adobe flash through the website as euthyfro mentioned, went with the APT option (that's the only one that provided a link) and opened with software centre. The result is youtube working partially (similar to sedan) but all other flash applications (games/videos) not loading at all. So reinstalling from adobe/software centre is better than nothing if youtube is what you want back.

---

### Post by drdanielfc on 2012-02-18
The problem is that Ubuntu uses the latest version of Flash player. Unfortunately, the latest means the *latest beta.* Many (incorrect) scripts assume it is not the current version because the version number is newer than the newest one. There really isn't  a solution. You could try downloading google chrome from their site which has flash bundled in or manually compile an older version.

---

### Post by Becks21 on 2012-02-18
Same problem here.. pulling in bugs by updates.. way to go Ubuntu

---

### Post by Saprissa on 2012-02-18
> **drdanielfc said:**
> The problem is that Ubuntu uses the latest version of Flash player. Unfortunately, the latest means the *latest beta.* Many (incorrect) scripts assume it is not the current version because the version number is newer than the newest one. There really isn't  a solution. You could try downloading google chrome from their site which has flash bundled in or manually compile an older version.
I have the problem in Chrome as well. 

Using version 17.0.963.56, the current stable release, I think.

I'm actually on Oneric, though my profile says Maverick.

---

### Post by lurgee on 2012-02-18
Similarish issues with Epiphany - won't play videos, claims there is a missing plugin.  Worked fine last week, but seems to have come unstuck following an update via update manager in the last couple of days.  Oddly, other browsers on the same computer (Firefox and Seamonkey) are working okay.  I'm running Lubuntu 10.10.

---

### Post by SixalivE on 2012-02-18
[http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)
I didn't change any of the preset options and flash now works as far as I can tell.

---

### Post by cyrus_the_virus on 2012-02-18
I have flash issues since that update last week as well. However, my problem is that I don't have any sound (sound works fine in other applications)

I tried reinstalling flash from the software center. I also tried to manually install an older version (11.1.102.55) by putting the libflashplayer.so file in /usr/lib/mozilla/plugins. Both did not solve the problem.

I discovered that google chrome uses HTML5 for youtube when the flash plugin is removed. So this is a work around. But this doesn't work for other sites using flash.

---

### Post by Saprissa on 2012-02-19
> **SixalivE said:**
> [http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)
I didn't change any of the preset options and flash now works as far as I can tell.

Worked for me, too.

Thanks a million!

---

### Post by Becks21 on 2012-02-19
> **SixalivE said:**
> [http://ubuntuforums.org/showthread.php?t=1491268](http://ubuntuforums.org/showthread.php?t=1491268)
I didn't change any of the preset options and flash now works as far as I can tell.

Thx a lot mate! As far as I can tell the Flash-Aid Mozilla-Plugin fixed everything (selected stable-flash).

Your post is worth the letters in gold [ton] ;)

---

### Post by azmyth on 2012-02-19
Thanks this fixed my flash problems too. Everytime I upgrade flash it seems to break something. This was tricky since some stuff sites worked and other sites didn't.

---

