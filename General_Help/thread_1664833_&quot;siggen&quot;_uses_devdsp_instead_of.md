---
title: "&quot;siggen&quot; uses /dev/dsp instead of ???"
date: 2011-01-11
forum: General Help
---

### Post by arvevans on 2011-01-11
Application "siggen" uses /dev/dsp instead of whatever the sound card is in Ubuntu/Gnome.

Can I make a link of /dev/dsp to the real sound card, and what should be the other end of that link?

---

### Post by arvevans on 2011-01-11
If you do a Google search for "Ubuntu /dev/dsp" you will find that there are a great many complaints about the loss of standard place for DSP access (/dev/dsp).  I found lots of well meaning explanations regarding Esound, Alsa, and so on, but nothing that actually restores the UNIX/Linux standard access point for sound devices (/dev/dsp).  Most of the recent complaints seem to blame Meercat (Ubuntu 10.10) for the failure, but there are also some older complaints that seem to indicate this deviation from standards may have occurred sporadically in earlier releases.

Most of the suggested fixes that I found on-line seem to focus on patching the application instead of fixing the source of this problem.  Unfortunately with many of the legacy applications that expect to use /dev/dsp for sound, there is no option to patch their configuration files for using some other sound access point.  

Did someone drop the ball in eliminating /dev/dsp, or is there a command or patch that restores /dev/dsp to it's expected location and function?

---

### Post by arvevans on 2011-01-11
Okay...after much digging around the Internet I finally found an explanation.  Seems that in Ubuntu 10.10 the system programmers saw fit to break the sound hook for hundreds of previously written applications by removing /dev/dsp and forcing users to use a proxy for sound card access:  

[INDENT][https://bugs.launchpad.net/bugs/579300]("https://bugs.launchpad.net/bugs/579300")[/INDENT]

Since the original writers of all those earlier applications may or may not still be living and available, this is a **major problem**.  Those earlier apps all point to /dev/dsp for audio system access, and most do not have config files or do not have config file hooks for linking to that proxy.

Somehow the developers at Debian need to provide a link or something that will re-activate all the now broken software packages that use /dev/dsp.

Also see bug#634211...this apparently is not an insignificant issue for those who use older applications on the Ubuntu 10.10 i386 release.

---

### Post by arvevans on 2011-01-12
bump

---

### Post by arvevans on 2011-01-13
This situation is much worse than most realize. In the Ubuntu repository are a great many legacy software programs which were hard-coded to use /dev/dsp to access the sound card. All these applications are now broken. Since they are hard-coded to use /dev/dsp there is no way short of re-writing the code to make them work with Ubuntu 10.10 and beyond.

At this point, the only thing I can say is "BEWARE THE UBUNTU REPOSITORY" because it contains a significant number of broken programs.

This type problem is not tagged by any "missing dependency" warnings, so you must download and install the programs in order to find that they don't work.

[I][COLOR="SeaGreen"]For some reason the forum admins have blocked further updates to this thread. 
I hope it is because they are working on the problem.......?[/COLOR][/I]

---

