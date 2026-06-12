---
title: "Package libqt3c102-mt is not installed."
date: 2006-03-13
forum: General Help
---

### Post by mitjab on 2006-03-13
sudo dpkg -i skype_1.2.0.18-1_i386.deb
Selecting previously deselected package skype.
(Reading database ... 91512 files and directories currently installed.)
Unpacking skype (from skype_1.2.0.18-1_i386.deb) ...
dpkg: dependency problems prevent configuration of skype:
 skype depends on libqt3c102-mt (>= 3:3.3.3.2); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing skype (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 skype

where i can get this package or how i can install skype?

Thx

---

### Post by Xian on 2006-03-13
Try enabling the PLF repos, as I believe they include skype:

```
deb http://cameronbergh.com/mirror/ubuntu/plf/ breezy free non-free
deb-src http://cameronbergh.com/mirror/ubuntu/plf/ breezy free non-free
```

---

