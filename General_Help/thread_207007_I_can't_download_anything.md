---
title: "I can't download anything"
date: 2006-07-01
forum: General Help
---

### Post by Loomy on 2006-07-01
I can't open any menus in firefox or download anything.  When I try to open the download menu this is the error I get.

> XML Parsing Error: syntax error
Location: chrome://mozapps/content/downloads/downloads.xul
Line Number 1, Column 1:ents.classes["@mozilla.org/network/io-service;1"].getService(Components.interfaces.nsIIOService);
^

This is my first time ever using linux.

---

### Post by Ubuntuud on 2006-07-01
Maybe you should try Epiphany to see if that works ("sudo aptitude install epiphany-browser").

---

### Post by jonrkc on 2006-07-01
And if Epiphany works OK and you can download through it -- then you might want to try:

```

sudo aptitude reinstall firefox

```

Whatever the error is, it has to do with the way Firefox gets displayed.  Strangely, I don't have anything like what your error message points to, in my Firefox installation (which I got straight from mozilla.org).  The only place on my system that there's anything to do with "mozapps" is in my Thunderbird directory, in its chrome section.  

Hmm.

---

