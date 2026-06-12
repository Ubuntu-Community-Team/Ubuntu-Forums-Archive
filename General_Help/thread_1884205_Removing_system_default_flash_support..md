---
title: "Removing system default flash support."
date: 2011-11-20
forum: General Help
---

### Post by ki4jgt on 2011-11-20
Hey guys,
On previous installs I've noticed during installation the user could install multimedia support so that I would run right out of the box. I enjoy this feature however, every time I would select the option, the flash-player would be a major pain. I'd go in and uninstall and install adobe. Then I just started leaving the option unchecked and installed after the system was setup. Yesterday, I wanted to hurry and get done with an installation and I checked the option again. Now I'm having problems with the system and would like to install adobe instead of whatever Ubuntu has placed in their restricted extras. I've forgotten what the flash player that's installed by default is called. Can someone help me out? The Internet keeps telling me Gnash :-( When i search for gnash in the repos, it says it's not installed.

---

### Post by mikewhatever on 2011-11-21
You can search through the installed packages:
```
dpkg -l | grep 'flash\|adobe\|gnash\|swfdec'
```

---

