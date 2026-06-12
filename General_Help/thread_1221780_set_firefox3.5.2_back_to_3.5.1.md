---
title: "set firefox3.5.2 back to 3.5.1"
date: 2009-07-24
forum: General Help
---

### Post by pigbird on 2009-07-24
Hi, I did an update today, and my firefox-3.5.1 became firefox-3.5.2 "pre". Is there anyway to set it back to 3.5.1 .

---

### Post by philinux on 2009-07-24
You must have a ppa in your sources as you are getting these updates.

Open Synaptic find firefox 3.5 click the versions tab. Highlight the one you want and then Package>force version.

Personally I would be happy with the pre release.

---

### Post by Bigtime_Scrub on 2009-07-24
I don't know of anyway of making a package go back to a previous version. You can delete Firefox 3.5.2 and just reinstall whatever version you like. (3.5.1)

---

### Post by lovinglinux on 2009-07-24
Run this to uninstall it:

```
sudo apt-get remove firefox-3.5
```

Then go to "System >> Administration >> Software Sources >> Third Party Software" and disable any item containing mozilla or firefox like this one:

```
http://ppa.launchpad.net/ubuntu-mozilla-daily/ppa/ubuntu
```

Then run this:

```
sudo apt-get update
```

Then finally this:

```
sudo apt-get install firefox-3.5
```

---

