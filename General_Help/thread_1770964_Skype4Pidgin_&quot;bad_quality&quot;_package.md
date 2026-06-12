---
title: "Skype4Pidgin &quot;bad quality&quot; package"
date: 2011-05-29
forum: General Help
---

### Post by NMFTM on 2011-05-29
Currently using Xubuntu 11.04 but had the same problem on Ubuntu.

When I go to install the Skype4Pidgin plugin via a deb from the [official source]("http://eion.robbmob.com/") I get a message saying that the package is of a bad quality with the following details:
```
Lintian check results for /home/ben/Desktop/skype4pidgin.deb:
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/locale/de/LC_MESSAGES/skype4pidgin.mo 1000/100 
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/locale/fr/LC_MESSAGES/skype4pidgin.mo 1000/100 
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/locale/it/LC_MESSAGES/skype4pidgin.mo 1000/100 
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/locale/ja/LC_MESSAGES/skype4pidgin.mo 1000/100 
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/locale/mk/LC_MESSAGES/skype4pidgin.mo 0/100 
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/locale/pl/LC_MESSAGES/skype4pidgin.mo 1000/100 
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/locale/pt/LC_MESSAGES/skype4pidgin.mo 1000/100 
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/locale/ru/LC_MESSAGES/skype4pidgin.mo 1000/100 
E: skype4pidgin: wrong-file-owner-uid-or-gid usr/share/pixmaps/pidgin/emotes/skype/theme 1000/100 
E: skype4pidgin: arch-independent-package-contains-binary-or-object usr/lib/purple-2/libskype.so 
E: skype4pidgin: arch-independent-package-contains-binary-or-object usr/lib/purple-2/libskype64.so 
E: skype4pidgin: arch-independent-package-contains-binary-or-object usr/lib/purple-2/libskype_dbus.so 
E: skype4pidgin: arch-independent-package-contains-binary-or-object usr/lib/purple-2/libskype_dbus64.so 
E: skype4pidgin: arch-independent-package-contains-binary-or-object usr/lib/purple-2/libskypearm.so 
```Ubuntu Software Center requires sudo privileges to install the package, so I don't see why user/group ID's would be a problem, especially since if you just click "Ignore and Install" it'll function as normal.

Installing the officially supported version of this package from the repos isn't an option as received IMs will only show up in the Skype chat window, not Pidgin's.

It doesn't seem to negatively effect anything so I'm hesitant to call it a problem. But I just figured I'd post and see if anyone had any input

---

