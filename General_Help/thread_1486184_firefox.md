---
title: "firefox"
date: 2010-05-17
forum: General Help
---

### Post by cowboy7305 on 2010-05-17
in latest version of ubuntu and FF 3.6.3 FF has stopped asking if you want to remember passwords,i have remember passwords activated in preferences

---

### Post by lovinglinux on 2010-05-17
Have you checked if the site is included in the Exceptions list, next to that option? If it is, then remove it.

If  the sites are not there, then type **about:config** in the address bar, then type **signon.rememberSignons** in the filter and make sure it is set as **true**.

If it is set as true, then open "Edit >> Preferences >> Privacy", then click the "Settings" button next to "Clear History when Firefox closes" and untick the "Saved Passwords" option.

If that doesn't help, then install [Password Exporter](https://addons.mozilla.org/en-US/firefox/addon/2848) and export your passwords using it. Then close Firefox, go to your Firefox profile folder (i.e. ~/.mozilla/firefox/<profile>) and delete or move the files **signons.sqlite** and **key3.db**. Restart Firefox and import your passwords back with Password Exporter.

---

