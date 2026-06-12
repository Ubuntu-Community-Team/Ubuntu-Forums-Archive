---
title: "Gnome Screensaver 2.14.2-0ubuntu1"
date: 2006-06-22
forum: General Help
---

### Post by SpEcIeS on 2006-06-22
It would seem that after updating gnome-screensaver-2.14.1 to 2.14.2 my screen savers do not work. Cannot lock session either.

Anyone else? :confused:

---

### Post by SpEcIeS on 2006-06-22
Got it. :)

Tried to recompile, but had no success. However, once gnome-screensaver was added to the session everything work fine now.

---

### Post by brodock on 2006-06-25
what do you mean by "added do session"?
i'm having exactly the same problem... i thought it was XGL...

could you give me a step-by-step instructions?
i tryied a full reinstall but got nothing... (full reinstall = reinstalling gnome-screensaver)

---

### Post by SpEcIeS on 2006-06-25
So I was not the only one. I also tried to reinstall, compiling the package again, but adding "***gnome-screensaver***" to the session startup did the trick.

Easy enough, go to your top panel menu and click on "**System**" -> "**Preferences**" -> "**Sessions**". Once you have found your way there select "**Startup Programs**", then select "**Add**", and the type in "**gnome-screensaver**". You could also add to you current session, but just log out and relogin. You will have you screensaver running.

---

### Post by brodock on 2006-06-26
thanks

---

