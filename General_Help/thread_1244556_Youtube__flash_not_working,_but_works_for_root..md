---
title: "Youtube / flash not working, but works for root."
date: 2009-08-19
forum: General Help
---

### Post by kaelidancer on 2009-08-19
Okay, I'm mystified.

Yesterday afternoon, flash video stopped working for me.  I get a grey box on all youtube-like videos in Firefox, running Ubuntu Hardy 32.

I've purged and reinstalled adobe-flashplugin several times, to no avail.

I also installed firefox 3.5, it gives the same result.  

If I "gksudo firefox" in a terminal, I get an instance running as root, and flash video works in it just fine.

I've pasted the libflashplayer.so file into every plugins folder I can find, both in my home directory, and in /usr/lib/

Any ideas?  It stopped working seemingly out of the blue.  Restarts have no apparent effect, either.

Thanks for your help!
K

---

### Post by kaelidancer on 2009-08-19
New info. Launched firefox from a terminal, and it gives me this error:

GTK1.x environments not supported. Exiting now.

---

### Post by kaelidancer on 2009-08-19
SOLVED!

It turned out to be FoxyTunes, a firefox plugin, that had updated itself and was apparently not getting along with Adobe flash player.  Removing the addon fixed my flash issue.

K

---

