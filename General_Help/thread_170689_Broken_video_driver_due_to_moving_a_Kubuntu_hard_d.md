---
title: "Broken video driver due to moving a Kubuntu hard drive to a new machine ..."
date: 2006-05-05
forum: General Help
---

### Post by em3raldxiii on 2006-05-05
Okay, my version of this problem is totally different from the HUNDREDS I have read about.  You will laugh at me I am sure, but you'll love this.  Hopefully someone can help me ...

Fatal server error:
no screens found

Quick & Dirty:

**Hard Drive in question:**
20GB Maxtor with Kubuntu 5.10 installed plus all kinds of server apps (LAMP server).  I figured it would be easier to migrate the server to a faster computer by moving the entire hard drive and then reconfiguring some hardware, as opposed to trying to back up and move the data (painful).

**Donor Computer:**
Celeron 466 with crappy onboard video (intel 810)

**Destination Computer:**
Intel P4 1.6 Ghz with an AGP Geforce 2 MX 400

Everything was autoconfigured (Linux is so damned smart!) except for the video card (because the drivers aren't open source, I imagine).

So I installed the drivers from this page:
[i][http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+graphics+driver](http://ubuntuforums.org/showthread.php?t=139264&highlight=nvidia+graphics+driver)[i], but many of the steps weren't applicable, so the driver is downloaded and "installed", but most of the configuration steps didn't work.

Shouldn't I just be able to edit the xorg.conf file to include the "correct" information regarding the drivers??  What if I was to just remove the entire section about the device?  Would *Xorg -configure* be able to reconfigure itself?

Thanks in advance.

Mike

PS.  Does anyone know WHY video card manufacturers haven't released the code to their drivers???  I understand proprietary technology and stuff, but there's gotta be more to gain from releasing it (and thereby getting much better driver support) than from keeping it to themselves (thereby alienating their hardware users).  Just a thought. :D

---

### Post by tseliot on 2006-05-05
Type:
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

and a your hardware should be automatically detected.

---

### Post by em3raldxiii on 2006-05-05
You Da Man!  I don't care what anyone else says, you are one smart cookie ;)

Haha, thanks so much, that worked perfectly.  I haven't come across any command like that at all in my searches so far.

If you happen to be curious to see the website I administer, check it here:  [www.anxietyofinfluence.ca](www.anxietyofinfluence.ca) ... it's for an alt-rock band reminiscent of Evanescence and Lacuna Coil.  Since you're from Italy I figured you might have heard of Lacuna Coil ... if not, well ... they're a fantastic alt-rock band. :D  I'm not exactly a pro with website development, but it's functional :D

---

