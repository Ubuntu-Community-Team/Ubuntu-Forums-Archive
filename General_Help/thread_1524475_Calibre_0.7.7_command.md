---
title: "Calibre 0.7.7 command"
date: 2010-07-05
forum: General Help
---

### Post by Axel-P on 2010-07-05
Hey!

I've installed calibre 0.7.7 in my machine, I have Karmic KDE 64. The problem is I can't start it with a single command. The command used to install it is:

```
sudo python -c "import urllib2; exec urllib2.urlopen('http://status.calibre-ebook.com/linux_installer').read(); main()"

```

And the installation location is /usr/local

Is there anyway to make calibre start with a single command ie: calibre instead of /usr/local/calibre/calibre

Thanks!
Axel

---

### Post by ankspo71 on 2010-07-05
Hi,
Try making a simlink to calibre in /usr/bin
```
sudo ln -s /usr/local/calibre/calibre /usr/bin/
```
I think that is all that needs to be done.
Hope that helps.

---

### Post by Axel-P on 2010-07-05
Yes that was all!

Thanks!

---

