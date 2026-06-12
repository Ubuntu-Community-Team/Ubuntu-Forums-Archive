---
title: "Flash problems with Firefox, but not Konqueror..."
date: 2009-07-19
forum: General Help
---

### Post by Mirge on 2009-07-19
I just installed Kubuntu 9.04 again.. 64 bit version. I installed kubuntu-restricted-extras, and Firefox 3.0.11...

I load Pandora in Firefox, after 4-5 songs (sometimes more, sometimes less)... the entire Flash portion of the page will turn a light gray color and won't work. Any new tabs I open with flash content will be the same gray color, and obviously not work.

I've had Pandora running in Konqueror for the past 3 hours and it hasn't had any issues at all... any advice on how to fix Firefox?

---

### Post by philcamlin on 2009-07-19
sudo apt-get purge firefox

sudo apt-get install firefox

does that do anything?

---

### Post by Mirge on 2009-07-19
> **philcamlin said:**
> sudo apt-get purge firefox

sudo apt-get install firefox

does that do anything?

Forgive my ignorance, but what's the point of that? Basically uninstalling/reinstalling Firefox? It's a clean install... literally this morning.

---

### Post by Mirge on 2009-07-20
bump... Konq has been running overnight & still going with Pandora going... Firefox messed up within a few songs.

---

### Post by Zorael on 2009-07-20
I believe the repository Flash is still a 32-bit flash wrapped with nspluginwrapper, thus prone to random spots of unreliability to obviously varying degrees depending on which browser you use. At least nowadays it only ends up as a grey box instead of crashing the whole browser, which it used to.

As it happens, there is a [still-alpha native 64-bit version](http://labs.adobe.com/technologies/flashplayer10/), Linux-only. I'd remove the one you have completely and try that alpha instead.

---

### Post by Mirge on 2009-07-20
> **Zorael said:**
> I believe the repository Flash is still a 32-bit flash wrapped with nspluginwrapper, thus prone to random spots of unreliability to obviously varying degrees depending on which browser you use. At least nowadays it only ends up as a grey box instead of crashing the whole browser, which it used to.

As it happens, there is a [still-alpha native 64-bit version]("http://labs.adobe.com/technologies/flashplayer10/"), Linux-only. I'd remove the one you have completely and try that alpha instead.

Thank you! I will try this shortly...

---

### Post by Mirge on 2009-07-20
Not real sure what to do with it.. it's a .so file... backed up my other occurrences of the file & copied this where existing versions were... now says Flash isn't installed (pandora).

---

### Post by Vaphell on 2009-07-20
does flash show up in about: plugins?

---

### Post by Mirge on 2009-07-20
Didn't get to check... I restored the original libflashplayer.so & it worked again...

---

### Post by Vaphell on 2009-07-20
i installed f10 alpha successfully, it fixed a lot of issues for me
only places where i can find libflashplayer.so in my hardy 64:
/usr/lib/firefox-addons/plugins/libflashplayer.so
/usr/lib/mozilla/plugins/libflashplayer.so

---

