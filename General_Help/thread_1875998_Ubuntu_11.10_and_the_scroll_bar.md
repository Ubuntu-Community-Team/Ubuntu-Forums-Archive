---
title: "Ubuntu 11.10 and the scroll bar"
date: 2011-11-05
forum: General Help
---

### Post by chemjeff on 2011-11-05
Hi all,
Is there a way to restore the pre-version-11 type of scroll bar on the windows?  I am not a big fan of the popout two-headed arrow for the scroll bar.  Thanks in advance!

---

### Post by batharoy on 2011-11-05
To Disable
```
sudo su
echo "export LIBOVERLAY_SCROLLBAR=0" > /etc/X11/Xsession.d/80overlayscrollbars
```
To Remove
```
sudo apt-get remove overlay-scrollbar liboverlay-scrollbar-0.1-0
```

Info From [http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html]("http://www.webupd8.org/2011/04/how-to-disable-overlay-scrollbars-in.html")

---

### Post by QuantikTar on 2011-11-26
It works but in 11.10 some applications are missing the up and down arrows (with the two methods : disabling or uninstalling).

I've seen that in the following :

Gwibber
Gedit
Nautilus

Any ideas?

Thanks

---

