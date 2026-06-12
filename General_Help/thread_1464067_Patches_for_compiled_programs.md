---
title: "Patches for compiled programs"
date: 2010-04-27
forum: General Help
---

### Post by Yarbo on 2010-04-27
I recently installed mplayer I compiled from svn, and now Ubuntu's package manager is showing security patches.  If I install these patches, will it mess up the version I compiled and installed?

---

### Post by jobix on 2010-04-27
Are you saying the package manager is showing security patches for mplayer? If so, did you not remove mplayer from the package manager when you compiled your own version from svn? Most likely things are going to get messed up if you use one version compiled outside the package manager and yet the package manager knows about some other version. It has to be clean. You should only be using one.

---

### Post by mc4man on 2010-04-27
> now Ubuntu's package manager is showing security patches.
security patches for what?

> If I install these patches, will it mess up the version I compiled and installed? 


There should be no effect

---

### Post by Yarbo on 2010-04-27
Security patches for MPlayer itself, which is why I was confused.  I made sure I removed every instance of MPlayer I could find in Synaptic before doing this, which is why I am confused.

By the way, I am on Hardy.

---

### Post by mc4man on 2010-04-27
How did you install your svn build?
If you used checkinstall or built a .deb package did you happen to version it below the hardy repo one? (in other words is update manager trying to update you back to the hardy repo mplayer - (last security update to that package was Wed, 08 Oct 2008 (mplayer (2:1.0~rc2-0ubuntu13.1)

---

### Post by andrew.46 on 2010-04-27
Hi Yarbo,

> **Yarbo said:**
> I made sure I removed every instance of MPlayer I could find in Synaptic before doing this, which is why I am confused.

Just to be sure you could run:

```
sudo find / -iname 'mplayer'
```

Andrew

---

