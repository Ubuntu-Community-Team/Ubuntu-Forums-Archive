---
title: "Installing Google Chrome"
date: 2012-05-29
forum: General Help
---

### Post by gmseed on 2012-05-29
Hi

I recently installed Ubuntu 12.04 and tried installing Chrome via the link:

[http://www.google.co.uk/chrome/index.html?hl=en&brand=CHNG&utm_source=en-hpp&utm_medium=hpp&utm_campaign=en&installdataindex=homepagepromo](http://www.google.co.uk/chrome/index.html?hl=en&brand=CHNG&utm_source=en-hpp&utm_medium=hpp&utm_campaign=en&installdataindex=homepagepromo)

I click the "Download Google Chrome" button and select the 32bit .deb radio button.

The installation hangs and fails to install.


Has anyone else experienced this issue?

Graham

---

### Post by zombifier25 on 2012-05-29
Can do it from the command line?
```
sudo dpkg -i packagename.deb
```

---

### Post by drmrgd on 2012-05-29
I found it easier to just add the Google-Chrome PPA.  That will also allow you to get updates when they are available through your regular package update method (CLI or Software Center).  The PPA instructions are here:

[http://www.ubuntuupdates.org/ppa/google_chrome](http://www.ubuntuupdates.org/ppa/google_chrome)

---

### Post by dik angga on 2012-05-29
good solution..
above me

---

### Post by anonymous5 on 2012-05-29
> **dik angga said:**
> good solution..
above me

Have you considered chromium? It's an open-source alternative.
(sudo apt-get install chromium-browser)

---

### Post by Deepak J on 2012-05-29
Go for chromium.

Its the base for Google Chrome. Between both of them there are just small differences. Like the tracking software and auto update system. Thats all.

You can install from Ubuntu software center and it'll get automatically updated.

---

