---
title: "One click to turn off computer?"
date: 2010-11-03
forum: General Help
---

### Post by t0p on 2010-11-03
I vaguely remember in 8.04 and 9.04, there was a way to set a preference so that when I clicked on *Shut Down*, the computer would shut down without asking me if I was sure.  But I can't remember how I set this preference, and much clicking on the panel and the *Turn off* button hasn't revealed how I do this thing.

So: is it still possible, in 10.04, to set things up so I can shut down without having to reply to  a pesky dialogue asking me if I'm sure?  How do I go about setting that preference?

Thanks.

---

### Post by s3MA00RRNY on 2010-11-03
$ gconf-editor

Navigate to /apps/gnome-session/options. The key logout_prompt seems to be what you want.

Correction: There seems to be another setting in /apps/indicator-session named "suppress-logout-restart-shutdown". Try that.

---

### Post by t0p on 2010-11-04
> **pcdude2143 said:**
> Correction: There seems to be another setting in /apps/indicator-session named "suppress-logout-restart-shutdown". Try that.

Thanks pcdude2143, that seems to have sorted out my "problem".  Most grateful.

---

### Post by gator2802 on 2010-11-04
> **t0p said:**
> Thanks pcdude2143, that seems to have sorted out my "problem".  Most grateful.
I have tried that as well and I have changed those settings in gconf and nothing has changed.  I have ubuntu 10.10 on a Dell 1545 laptop.
Thanks

---

### Post by CompBio on 2011-03-02
Same here -- I've made that change and my Shut Down and Restart both give me that infuriating dialog.  (Ubuntu Netbook Remix 10.10)

The change I made was:

sudo gconf-editor
apps -> gnome-session -> options -> logout_prompt OFF
apps -> indicator-session ->  suppress_logout_restart_shutdown ON

These have no effect at all.

Sheesh -- what's next for Ubuntu, a dancing paperclip?  :mad:

---

### Post by CompBio on 2011-03-02
Holy crap -- I decided to go methodically through all the apps in Netbook Remix and stumbled onto the pulldown menu on the Login Screen Settings dialog.  At least on my computer the options are: Ubuntu Desktop Edition / Ubuntu Netbook Edition / Recovery Console / User Defined Session / Ubuntu Desktop Edition (Safe Mode)

I selected Ubuntu Desktop Edition and voila!  No more Netbook.  I'm much happier now...  \\:D/

---

