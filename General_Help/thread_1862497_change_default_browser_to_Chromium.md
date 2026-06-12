---
title: "change default browser to Chromium?"
date: 2011-10-16
forum: General Help
---

### Post by shaviro on 2011-10-16
How can I change the default browser in Oneiric from Firefox to Chromium? When I go to System Settings ---> System Info ---> Default Applications, Firefox is the only choice listed. I have installed Chromium, and I use it all the time, but how can I get it as an alternative in Default Applications?

thanks

---

### Post by peter d on 2011-10-17
Go into Chromium browser preferences (click on the spanner, chose preferences) and set it as the default.

---

### Post by shaviro on 2011-10-18
> **peter d said:**
> Go into Chromium browser preferences (click on the spanner, chose preferences) and set it as the default.

I have done this, but it doesn't seem to effect the whole system. If I click on a link in an email, for instance, it still opens Firefox instead of going to the link in Chromium.

---

### Post by blueridgedog on 2011-10-18
Install via synaptic or run if installed, gconf-editor, then run gconf-editor and go to:

/desktop/gnome/applications/browser/

and replace the firefox line with:

/opt/google/chrome/google-chrome

(or your path to chrome if different).

---

