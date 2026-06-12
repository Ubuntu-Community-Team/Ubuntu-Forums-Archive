---
title: "Save desktop session with reboot command"
date: 2010-05-01
forum: General Help
---

### Post by terranair on 2010-05-01
Hi!
When I do sudo reboot/poweroff in Konsole the KDE session does not get saved.
But when I do it through the KMenu it does.
Can someone tell me how this is being done? Are there scripts involved?
If not can this be scripted?
10x!

---

### Post by sisco311 on 2010-05-01
KDE3:
```
dcop ksmserver default saveCurrentSession
```

KDE4:
```
dbus-send --dest=org.kde.ksmserver /KSMServer org.kde.KSMServerInterface.saveCurrentSession
```

---

### Post by terranair on 2010-05-02
Nope, it does not work.
Any other ideas?

---

