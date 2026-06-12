---
title: "Firefox bookmark restore fails"
date: 2011-12-16
forum: General Help
---

### Post by rdh61 on 2011-12-16
After an update I found my Firefox bookmarks had disappeared. When I try to restore them from a backup file I get the following error message:

[B][I]A script on this page may be busy, or it may have stopped responding. You can stop the script now, or you can continue to see if the script will complete.

Script: file:///usr/share/mozilla/extensions/%7Bec8030f7-c20a-464f-9b0e-13a3a9e97384%7D/bindwood@ubuntu.com/modules/bindwood.jsm:833[/I][/B]

If I elect to allow the script to continue, the same error message keeps popping up. Any ideas?

Many thanks.

---

### Post by lovinglinux on 2011-12-16
It is the Bindwood add-on, that allowed Ubuntu One to sync bookmarks. That functionality of Ubuntu One has been discontinued. Uninstall bindwood and you should regain the ability to restore backups.
If you are using Ubuntu 11.10 then you can use this command:

```
sudo apt-get remove xul-ext-bindwood
```

---

### Post by rdh61 on 2011-12-16
Thanks. Solved.

---

