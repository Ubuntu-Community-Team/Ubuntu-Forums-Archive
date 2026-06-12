---
title: "Set Firefox Homepage for all users"
date: 2010-06-23
forum: General Help
---

### Post by dmonty on 2010-06-23
We are doing a mass kubuntu roll-out for 50+ schools.  I would like to be able to change the default homepage for all users from start.ubuntu.com to be the school's website.

With 9.10 I would set /etc/firefox-3.0/pref/ubufox.js
```
pref("browser.startup.homepage", "file:/etc/firefox-3.0/pref/homepage.properties");
```
Then /etc/firefox-3.0/pref/homepage.properties
```
browser.startup.homepage=http://www.sd73.bc.ca/
```

This now does not work in 10.04.  I've tried all sorts of variations but cant get it to stick.

---

### Post by dmonty on 2010-06-23
Figured it out - ubufox plug in extension moved the config file settings...

/etc/xul-ext/ubufox.js
```
pref("browser.startup.homepage", "file:/etc/xul-ext/homepage.properties");
```
/etc/xul-ext/homepage.properties
```
browser.startup.homepage=http://www.sd73.bc.ca/
```

---

