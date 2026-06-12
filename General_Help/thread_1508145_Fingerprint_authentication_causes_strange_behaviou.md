---
title: "Fingerprint authentication causes strange behaviour"
date: 2010-06-12
forum: General Help
---

### Post by Fibonacci on 2010-06-12
Hello.

I've recently noticed that whenever I log in via fingerprint reader (AES2501), my system behaves strangely.
For example, the Gnome panels take almost a full minute to appear after everything else has been loaded, and there's no NetworkManager icon in the panel - even though nm-applet (and thus NetworkManager) is running as shown by top; that can be (partially) solved by killing NetworkManager, restarting dbus, and then manually running NetworkManager.
None of that happens when logging in using a password.

Short of not using my fingerprint reader, what can I do?

---

### Post by Fibonacci on 2010-06-14
Does anyone else experience this problem too?

---

### Post by Fibonacci on 2010-06-17
Which package should I report the bug against?

---

### Post by Fibonacci on 2010-06-18
Reported: [https://bugs.launchpad.net/ubuntu/+bug/596116](https://bugs.launchpad.net/ubuntu/+bug/596116)

---

