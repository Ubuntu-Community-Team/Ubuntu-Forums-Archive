---
title: "Update Manager Keeps Suggesting Updates I've Already Installed"
date: 2009-08-09
forum: General Help
---

### Post by tacantara on 2009-08-09
[COLOR=Red]**SOLVED :)**[/COLOR]

For the past couple of weeks, I've been getting the same updates listed under "Other Updates" every day when my system checks for new updates on Update Manager.  These updates are:

***Firefox; Firefox-3.5; Firefox-3.5-branding; Google-Chrome-Unstable;  Xulrunner-1.9.1; Xulrunner-1.9.1- Gnome-Support***

I've even attempted to download these "updates" only to find them listed again the next day.  Does anyone have any theories as to why this is happening, and how it can be corrected?

---

### Post by Barafu Albino Cheetah on 2009-08-09
Something prevents it from installing. try sudo aptitude full-upgrade.

---

### Post by tacantara on 2009-08-09
Thank you, Barafu Albino Cheetah, for the advice.  It worked like a charm...it just took a while for the downloads to complete, because I'm on a really slow ISP here.  Otherwise, all is well.

---

