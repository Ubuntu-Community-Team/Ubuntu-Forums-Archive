---
title: "Chrome not remembering me?"
date: 2009-12-28
forum: General Help
---

### Post by michaelzap on 2009-12-28
Chrome beta (from the Google beta PPA) isn't remembering me between sessions. So for example when I click on my Ubuntu Forums bookmark I'm not logged in (although it will autofill the fields for me and log in normally. This happens with every site, so perhaps there's some sort of permissions issue with cookies (although other prefs are remembered just fine)?

I was using the daily build of Chromium before this, but I uninstalled it and removed the daily build PPA from my sources because it was resizing randomly on Flash sites and generally being unpredictable (although it did remember my logins).

Anyone else experiencing this or have any idea how to resolve it?

---

### Post by michaelzap on 2010-01-02
bump?

---

### Post by michaelzap on 2010-01-02
Apparently my Cookies database in /home/username/.config/chromium/Default/ was corrupt. I deleted it and let Chromium recreate a new one, and now it works as it should. Hopefully this will help someone else.

---

### Post by sanjivr on 2012-07-27
As michaelzap has mentioned this happens when the cookies database is corrupt. However the Cookies database can reside either in

/home/{username}/.config/chromium/Default or
/home/{username}/.config/google-chrome/Default

If you already have signed into chrome and are syncing your chrome data, please disconnect first and only then should you delete the local profiles under ~/.config/chromium and ~/.config/google-chrome.

Restart Chrome and re-signin to Chrome. The sync will take care of restoring your data.

---

### Post by wildmanne39 on 2012-07-27
Hi, this is an old thread so it has been closed, please do not post in threads that are a year or more old, and thanks for sharing.

---

