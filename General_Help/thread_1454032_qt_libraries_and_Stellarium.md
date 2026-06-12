---
title: "qt libraries and Stellarium?"
date: 2010-04-14
forum: General Help
---

### Post by rebeltaz on 2010-04-14
I installed Stellarium through Synaptic, but when I ran it, the screen was blank except for the toolbars and when I rolled my mouse over those, the old images were not erased before the new images were drawn, so the screen became a cluttered mess. And when I clicked on the configure screen to see if there was anything there that might help (there wasn't), I tried to close that window, but even though the program thought the window closed, it didn't get erased from the screen. 

Through some research, I found a discussion that the QT v4.6 libraries were needed. I did a quick look at dpkg for qt packages and came up with this:

```

derek@eMachines:~$ sudo dpkg -l | grep qt
[sudo] password for derek: 
ii  libavahi-qt3-1                             0.6.25-1ubuntu5.1                          Avahi Qt 3 integration library
ii  libdbusmenu-qt1                            0.2.2-0ubuntu2~karmic1~ppa1                a Qt library that implements the DBusMenu sp
ii  libpolkit-qt0                              0.9.3-0ubuntu1~karmic1~ppa1                PolicyKit-qt library
rc  libpoppler-qt2                             0.12.0-0ubuntu2.1                          PDF rendering library (Qt 3 based shared lib
ii  libpoppler-qt4-3                           0.12.0-0ubuntu2.1                          PDF rendering library (Qt 4 based shared lib
ii  libqt3-mt                                  3:3.3.8-b-5ubuntu3                         Qt GUI Library (Threaded runtime version), V
rc  libqt4-assistant                           4.5.0-0ubuntu4                             Qt 4 assistant module
ii  libqt4-dbus                                4:4.6.2-0ubuntu1~karmic1~ppa2              Qt 4 D-Bus module
ii  libqt4-designer                            4:4.6.2-0ubuntu1~karmic1~ppa2              Qt 4 designer module
rc  libqt4-help                                4.5.0-0ubuntu4                             Qt 4 help module
ii  libqt4-network                             4:4.6.2-0ubuntu1~karmic1~ppa2              Qt 4 network module
ii  libqt4-opengl                              4:4.6.2-0ubuntu1~karmic1~ppa2              Qt 4 OpenGL module
ii  libqt4-phonon                              4:4.6.2-0ubuntu1~karmic1~ppa2              transitional package for Qt 4 Phonon librari
ii  libqt4-qt3support                          4:4.6.2-0ubuntu1~karmic1~ppa2              Qt 3 compatibility library for Qt 4
ii  libqt4-script                              4:4.6.2-0ubuntu1~karmic1~ppa2              Qt 4 script module
ii  libqt4-sql                                 4:4.6.2-0ubuntu1~karmic1~ppa2              Qt 4 SQL module
ii  libqt4-sql-mysql                           4:4.6.2-0ubuntu1~karmic1~ppa2              Qt 4 MySQL database driver

```

So how do I install the QT v4.6 packages and do I need to remove anything listed above? Will 4.6 coexist with whatever I have now or will it replace it or what? ARRG!

Thanks....

Better yet... when or where can I find either 10.3 or 10.4 of the binary package of Stellarium for Karmic?

---

