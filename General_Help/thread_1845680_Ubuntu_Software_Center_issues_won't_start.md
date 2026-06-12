---
title: "Ubuntu Software Center issues: won't start"
date: 2011-09-17
forum: General Help
---

### Post by user sam on 2011-09-17
Trying to start software-center gives me this error:
```
2011-09-17 11:28:17,042 - softwarecenter.fixme - WARNING - logs to the root logger: '('/usr/share/software-center/softwarecenter/netstatus.py', 73, '__init_network_state')'
2011-09-17 11:28:17,042 - root - WARNING - failed to init network state watcher 'org.freedesktop.DBus.Error.ServiceUnknown: The name org.freedesktop.NetworkManager was not provided by any .service files'

```
It gives me a blank window titled Ubuntu Software Center. I can't do anything with it. I can still use gksu to get to it, but I can't access anything as a normal user. I don't understand what's wrong...
can anyone point me in the right direction?

---

### Post by c5f8 on 2011-12-28
I have Ubuntu 11.10. I tried installing Amazon MP3 Downloader for Ubuntu 9.04. The installer gave a message needing libboost 1.34. Then the system cleaned up the files.

Now my Ubuntu Software Center only has a blank screen. Anyone know how to fix this?

---

### Post by c5f8 on 2011-12-28
> **c5f8 said:**
> I have Ubuntu 11.10. I tried installing Amazon MP3 Downloader for Ubuntu 9.04. The installer gave a message needing libboost 1.34. Then the system cleaned up the files.

Now my Ubuntu Software Center only has a blank screen. Anyone know how to fix this?



I just booted into the recovery mode, then entered fsck, then resume.
Now Ubuntu Software Center application appears normal.

---

