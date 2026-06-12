---
title: "Why on earth??? [Natty problems]"
date: 2011-08-23
forum: General Help
---

### Post by tubunu on 2011-08-23
Well, here I am, having finally done a fresh install from Lucid 10.04 to Natty 11.04. I've been using Ubuntu for over 7 years, so I can't call myself a newbie, but I feel like one after this upgrade. 

Here's what might stop a new user from enjoying Ubuntu.

I did a fresh install and then decided I don't need a couple of packages, like Orca, Ekiga, Empathy, etc. I do realize some of them are a part of the gnome desktop and if removed, the system might not function correctly. 

**My major complaint is WHY ON EARTH is the user allowed to remove those packages from within the Software Center only to find out upon restart/reboot that the desktop is broken?** (i.e. title bars of all windows are missing, compositing fails to work even if enabled via gconf-editor, opening personal folders in Nautilus is impossible - giving some kind of an error..). Why doesn't the user get a warning of some kind that they are about to remove core packages required for the desktop to work?

Again, I should have known better, but what about a new Ubuntu user that has no knowledge of that kind whatsoever? This is ridiculous. I now am reinstalling the whole gnome package in the hope of getting things to work properly. Arrrgh.

---

### Post by tubunu on 2011-08-23
OK, I reinstalled the whole "gnome" package, but it didn't help. Can anyone point me in the right direction? I'm including a screenshot of the mess I have now. Thanks in advance.

---

### Post by coffeecat on 2011-08-23
> **tubunu said:**
> OK, I reinstalled the whole "gnome" package, but it didn't help.

Well, let's hope that didn't make things worse. The gnome package is not the "official" Ubuntu-configured one. Install the meta-package ubuntu-desktop which will hopefully bring is as dependencies everything that's missing. 

You may have to mark it for re-installation if it wasn't taken out by the packages you uninstalled.

---

### Post by tubunu on 2011-08-23
> **coffeecat said:**
> Well, let's hope that didn't make things worse. 

I did all that plus reinstalled ubuntu-desktop and things are still broken. I can't get the title bars to show, compositing doesn't want to be enabled, and everything behaves funny. How I love this... I so don't wanna reinstall the system.. maybe there's an easy fix for that? Thank you in advance.

---

### Post by CatKiller on 2011-08-23
Ubuntu hasn't been going for seven years. New users don't generally remove random packages, so they're unlikely to be in the situation you are. You're told which packages are going to be removed at the time that you do it. Other than asking if that's what you want, which it does, how is it supposed to know that you're lying? The gconf key to tell Metacity to try compositing isn't the same as the default setup, which doesn't use Metacity at all but uses Compiz instead. The *gnome* metapackage isn't installed by default anyway. *ubuntu-desktop* is more like the default setup.

You haven't given us much information to go on. You said that you didn't need a "couple" of packages and then listed at least three that you wanted to remove. You say that you can't open folders in Nautilus but don't give any details of the symptoms - "some kind of error." You also don't say which session you've logged into - Unity, Classic, or whatever.

```
compiz --replace
``` might go some way to identifying quite how much you've managed to remove. CompizConfig Settings Manager will be useful for re-enabling the effects and the Unity plugin once you've managed to get Compiz running again.

---

### Post by 3rdalbum on 2011-08-23
Create a new user account, log into that, and see how things behave.

---

### Post by qamelian on 2011-08-23
> **CatKiller said:**
> Ubuntu hasn't been going for seven years. 
Close enough to seven. The first release was October 2004, so we're only about 2 months and a bit from 7 years.

---

