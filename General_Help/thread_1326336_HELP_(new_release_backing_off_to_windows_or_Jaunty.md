---
title: "HELP (new release/ backing off to windows or Jaunty)"
date: 2009-11-14
forum: General Help
---

### Post by BarefootSoul83 on 2009-11-14
I recently put Ubuntu on a friends machine...unfortunately they have the ONLY datacard known to man that is not plug n play w/ Ubuntu.... So, I thought, maybe the new release will have a patch? The new release crashed my graphics...

I'm trying to just put Windows XP back on it...but when it gets to the "Loading Windows" (right before you format/partition) it gives me the blue screen of death...

Gparted live crashes

Ubuntu live (Jaunty) wont boot?

HELP! Can I back off the recent Upgrade? or How do I get Windows XP back on here?

---

### Post by gdonwallace on 2009-11-14
Sounds similar to a problem I was having, Ubuntu no matter the version would not boot up.  It would install but that was as far as it got.

What I had to do was install something different, that would overwrite the MBR and then re-install Ubuntu.  I installed OpenSolaris (Unix variant of Solaris) I was then able to install Ubuntu and run it with no problems.  My issue was the MBR, but I also think other thinks where effected because I was running FSCK on a mounted hard drive.  

Installing OpenSolaris is very similar to Ubuntu.  After its done and rebooted, I would try the Ubuntu install again.

I know its a pain, but it worked for me as I did not have access to the internet and just happened to have the OpenSolaris liveCD.

Good luck

---

### Post by cmcanulty on 2009-11-14
Had similar problem with a dell inspiron 9300 if I could disable all desktop effects it would work but I had to install another linux 1st, then Ubnuntu a pain but did work.

---

