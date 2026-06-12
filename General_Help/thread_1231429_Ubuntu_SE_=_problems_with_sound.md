---
title: "Ubuntu SE = problems with sound"
date: 2009-08-04
forum: General Help
---

### Post by Clyssus on 2009-08-04
[LEFT]I installed the[COLOR=Red] [Ubuntu Satanic Edition]("http://ubuntusatanic.org/installation.php") [/COLOR]through adding the repository... then I lost sound. I was able to restor playback for exaile but still don't have it for flash players online such as youtube, my space music, etc... I'm running Ubuntu 9.04 on an Emachine T5082 using Firefox, can anybody help?  :confused:
[/LEFT]

---

### Post by jocampo on 2009-08-04
Do you have sound or you do not at all? asking because if can't hear anything at all, could be a driver issue which was corrupted by your Satanic and unsupported version, maybe a God's punishment? hahahaa, kidding ...

If you have sound on some applications and not in others, maybe you need to re-install those plug-ins again...

---

### Post by Clyssus on 2009-08-04
[quote=jocampo]maybe a God's punishment? hahahaa, kidding ...[/quote]
:lolflag:

I have playback with my media players (Exaile & Rhythmbox) and when I login... but not for flash players on the web such as youtube, myspace music, google video, etc....

---

### Post by Bölvaður on 2009-08-04
if you have many audio devices and use pulse please install [pulse audio device chooser  ]("apt:padevchooser")(by clicking this link), then click on the icon that comes in applications &#8594; sound... &#8594; pulse audio device chooser, see the icon in your tray pop up and right click it, click volume control.

alternatively check System &#8594; Preferences &#8594; Sounds

and make sure all applications are using OSS, alsa or pulse (only of of them that is)

---

### Post by Clyssus on 2009-08-04
I already set all of the options to "**OSS**" in the** sound **menu, this is how I got the playback to work on Exaile & Rhythmbox, though I'm still having issues with audio on flash players on the web... I'll give your suggestion a try...

---

### Post by Clyssus on 2009-08-04
Tried your suggestion with no success... is there any thing else I can do? I've also discovered that I have no audio with any video media even with Movie Player!

---

