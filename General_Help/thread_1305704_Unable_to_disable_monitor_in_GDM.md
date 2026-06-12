---
title: "Unable to disable monitor in GDM"
date: 2009-10-30
forum: General Help
---

### Post by asaz989 on 2009-10-30
I'm running a semi-cannibalized Thinkpad Z61t - the built-in LCD (dead) is physically removed, and I use a big ol' Acer 1680x1050 monitor.

Problem is, I can't figure out how to get GDM to use **only** the external monitor - it insists on setting the resolution to what it would be if - per X defaults - I were mirroring my two screens (the laptop built-in was 1280x800).

I've managed to set this up so it works at optimal resolution for my GNOME desktop (just went to System->Preferences->Display), but GDM graphics settings are based on system-wide X settings. How do I change these so that X doesn't try to mirror my two displays on startup, and only considers the one that's actually working when deciding the resolution?

---

