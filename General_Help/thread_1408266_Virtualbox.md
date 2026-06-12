---
title: "Virtualbox"
date: 2010-02-16
forum: General Help
---

### Post by Corasaaa on 2010-02-16
When i've tried to install Virtualbox-3.1 it has sent me an error:
________
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.5.3really4.5.2-0ubuntu1_amd64.deb](http://it.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtcore4_4.5.3really4.5.2-0ubuntu1_amd64.deb) 403  Forbidden
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.5.3really4.5.2-0ubuntu1_amd64.deb](http://it.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-network_4.5.3really4.5.2-0ubuntu1_amd64.deb) 403  Forbidden
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.5.3really4.5.2-0ubuntu1_amd64.deb](http://it.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqtgui4_4.5.3really4.5.2-0ubuntu1_amd64.deb) 403  Forbidden
Failed to fetch [http://it.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.5.3really4.5.2-0ubuntu1_amd64.deb](http://it.archive.ubuntu.com/ubuntu/pool/main/q/qt4-x11/libqt4-opengl_4.5.3really4.5.2-0ubuntu1_amd64.deb) 403  Forbidden
________
Please help me i need work with Ubuntu and Windows on Virtualbox.
ps: Sorry for my bad english.

---

### Post by El Zoido on 2010-02-16
Not sure what's the reason for this error, but anyway I would suggest using the repos from virtualbox.org for the newest non-ose version (ose version from ubuntu repos is missing for example usb support for virtual machines):
[http://www.virtualbox.org/wiki/Linux_Downloads]("http://www.virtualbox.org/wiki/Linux_Downloads")

You can find instructions for adding the repos on this site, too.

Edit: Sorry, I guess I misread your post, seems your problem is not Virtualbox but some dependencies!

---

### Post by arubislander on 2010-02-16
Alternatively you could try using another mirror. You are usiing [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) at the moment, maybe another italian mirror might work.

---

