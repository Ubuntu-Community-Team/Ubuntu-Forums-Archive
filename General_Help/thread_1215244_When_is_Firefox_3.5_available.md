---
title: "When is Firefox 3.5 available?"
date: 2009-07-16
forum: General Help
---

### Post by geovino on 2009-07-16
When will Firefox 3.5 be in the repos?

oops! it's already there :)

---

### Post by elliotn on 2009-07-16
Havent this been discussed b4

---

### Post by starcraft.man on 2009-07-16
It already is, make sure universe repos are enabled. The package is :

```
firefox-3.5
```

Nothing complicated to it. Install by your preferred means, see sig if you need help on that.

And ya, please search, this has been asked often. Really.

---

### Post by dj-toonz on 2009-07-17
The version Of firefox-3.5 in the repos is the beta version (not the final version) it won't over-ride firefox 3.0.11 what jaunty 9.04 has now. If you want the default Ubuntu version, you'll have to wait till October for ubuntu 9.10 or you can use ubuntuzilla from [http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/) what will do everything for you, it can install firefox-3.5 and set up the sym-links & thunderbird 3 aswell if you want

---

### Post by bodhi.zazen on 2009-07-17
Just FYI:

There is an as of yet unpatched security hole in FF 3.5 so you may want to wait a few days until there is a patch.

[http://secunia.com/advisories/35798/](http://secunia.com/advisories/35798/)

---

### Post by Crunchy the Headcrab on 2009-07-17
I'm using FF3.5 in Fedora Leonidas (and windows of course) and it's really not that different from 3.11 anyway.  That is to say the new features don't really impress me, so there isn't really a need to update.

---

### Post by bodhi.zazen on 2009-07-17
> **Crunchy the Headcrab said:**
> I'm using FF3.5 in Fedora Leonidas (and windows of course) and it's really not that different from 3.11 anyway.  That is to say the new features don't really impress me, so there isn't really a need to update.

FF 3.5 is noticeable faster then FF 3.11 both in the published benchmaks and on every OS I have compared the two on.

[http://technologizer.com/2009/06/30/firefox-3-5-review/](http://technologizer.com/2009/06/30/firefox-3-5-review/)

That was the top of the list on google, but other published benchmarks are similar.

---

### Post by lovinglinux on 2009-07-17
The 4 most popular methods of installation of Firefox 3.5 (Psychocats, Ubuntuzilla, Repository, Shiretoko/Swiftfox) are available in the "Install Other Versions" section of the [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567). 

There is also a detailed explanation of each installation method provided, comparing the most important differences. I personally tested all of them and they work like a charm, but I recommend methods 1 (Psychocats) and 2 (Ubuntuzilla).

---

### Post by Alnico on 2009-07-17
I'm having loads of problems with Firefox 3.5

* In Windows (dual boot), it takes ages to load, and whets up about 56 MB of memory to load.
* In Ubuntu, 
** The release from the archives is a pre-release (why would anyone want a old release ??) I compiled the original instead.
** Flash does not work on Firefox for 64 bit systems. You have to configure it yourself
** Downloaded applications do not open. Try downloading a PDF, and opening it from the download list... it won't open 
** Weird behaviour of tabs suddenly breaking free and opening in a new window.

---

### Post by lovinglinux on 2009-07-17
> **Alnico said:**
> * In Windows (dual boot), it takes ages to load, and whets up about 56 MB of memory to load.

56 MB of memory on start is pretty normal. Perhaps your Widows partition is fragmented and thus slowing down Firefox launch. It could also be due to junk data on sqlite databases. See Database Optimization section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

I read that Firefox 3.5 in Windows is faster than in Ubuntu.


> **Alnico said:**
> ** The release from the archives is a pre-release (why would anyone want a old release ??) I compiled the original instead.

No, it isn't. If you sources are updated, then it should install the latest version. If you are talking about the description in the Add/Remove manager, then just ignore it. Open Shiretoko, then go to "Help >>About" and you will see.

Nevertheless, I compile it myself too and I couldn't be happier with 30% performance boost from compiling optimizations.

> **Alnico said:**
> ** Flash does not work on Firefox for 64 bit systems. You have to configure it yourself

I don't have 64bit. so I can't comment.


> **Alnico said:**
> ** Downloaded applications do not open. Try downloading a PDF, and opening it from the download list... it won't open

It opens for me. Do you have [PDF Download](https://addons.mozilla.org/en-US/firefox/addon/636) extension?

> **Alnico said:**
> ** Weird behaviour of tabs suddenly breaking free and opening in a new window.

No problems here whatsoever. The only issue I had was the crash when viewing YouTube on fullscreen, but I fixed it with a small hack. See troubleshooting section of [**[COLOR="DarkRed"]Firefox optimization and troubleshooting thread[/COLOR]**](http://ubuntuforums.org/showthread.php?t=1193567)

> **elliotn said:**
> Havent this been discussed b4

[There was only 45 threads about Firefox 3.5 on the first week after release.](http://ubuntuforums.org/showthread.php?t=1200781)

BTW, I give less than 24 hours until someone complains about the Shiretoko name on this thread too :)

---

### Post by TheNosh on 2009-07-17
> **lovinglinux said:**
> BTW, I give less than 24 hours until someone complains about the Shiretoko name on this thread too :)

i'd argue that the fact that it's still using that name is note worthy. not a horrible thing, but worth metioning.

---

### Post by lunarmelody on 2009-07-17
> **Alnico said:**
> ** Flash does not work on Firefox for 64 bit systems. You have to configure it yourself


For a 64-bit system, you need to download the flash player plugin from [here](http://get.adobe.com/flashplayer/) in tar.gz format.  It should give you a file install_flash_player_10_linux.tar.gz.  Extract this file then cd to the directory you extracted it to.  Copy the file libflashplayer.so to /usr/lib/mozilla/plugins and restart firefox.

---

### Post by scouser73 on 2009-07-17
I've downloaded Firefox 3.5 using this tutorial: [http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/]("http://www.kabatology.com/07/01/a-single-command-install-of-firefox-3-5-on-ubuntu/")

And it's not Shiretoko.

---

### Post by Crunchy the Headcrab on 2009-07-17
Well slap me thrice and hand me to my mother!  It turns out I had a messed up hosts file that was affecting firefox.  It is SUPER fast now.  Faster than windows ff3.5.  Nothing but love.  I've gotta say I'm loving Linux right now.  I have a screaming fast OS that is customized how I like it ::D

---

### Post by lovinglinux on 2009-07-17
> **Crunchy the Headcrab said:**
> I've gotta say I'm loving Linux right now.

No, no. I'm loving linux. :)

---

