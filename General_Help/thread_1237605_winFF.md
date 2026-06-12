---
title: "winFF"
date: 2009-08-11
forum: General Help
---

### Post by Silvernail on 2009-08-11
I used synaptic package manager to install 'winFF' but get this error.

winff:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1.1 is to be installed

What next?

---

### Post by Silvernail on 2009-08-11
I used synaptic package manager to install 'winFF' but get this error.

winff:
  Depends: libgtk2.0-0 (>=2.14.1) but 2.12.9-3ubuntu5 is to be installed
  Depends: libpango1.0-0 (>=1.21.6) but 1.20.5-0ubuntu1.1 is to be installed

What next?

---

### Post by Rocket2DMn on 2009-08-11
Threads merged - please don't post duplicate threads, it isn't fair to the community members helping out, and as you can see doesn't really result in getting more or better help.
Thank you.

---

### Post by WRDN on 2009-08-11
Install the packages it depends upon:

```
sudo apt-get install libgtk2.0-0 libpango1.0-0
```

---

### Post by mc4man on 2009-08-11
You should mention what release of ubuntu you're using  (if not still hardy 

did you add a ppa to your sources? (like the winff ppa

Your showing hardy versions of libgtk2.0-0, ect. installed and trying to install an intrepid or jaunty version of winff

Post your sources.list

```
cat /etc/apt/sources.list
```

---

