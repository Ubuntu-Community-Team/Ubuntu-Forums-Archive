---
title: "kedit and kwrite errors"
date: 2006-02-14
forum: General Help
---

### Post by equal on 2006-02-14
every time I use kedit, I get the following errors:

```

phil@kubuntu:~$ sudo kedit /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.

```

but it still grants me access to the file. 

on the other hand, with kwrite I get:

```

phil@kubuntu:~$ sudo kwrite /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kdeinit: Can't connect to the X Server.
kdeinit: Might not terminate at end of session.
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kded: cannot connect to X server :0.0
kded: ERROR: KUniqueApplication: Registering failed!
kded: ERROR: Communication problem with kded, it probably crashed.
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KMimeType): WARNING: KServiceType::offers : servicetype KTextEditor/Plugin not found
kio (KSycoca): WARNING: Found version 79, expecting version 93 or higher.
kio (KSycoca): WARNING: Outdated database found
kio (KSycoca): ERROR: No database available!
kio (KSycoca): ERROR: No database available!
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

```

followed by a popup saying: "Sorry KWrite
Could not find mime type
application/octet-stream"

Any clues, oh wise KDE wizards? :)

---

### Post by equal on 2006-02-14
One thing I notice, it isn't asking me for my password, even though I entered a sudo command. Odd, no?

---

### Post by ivanhelguera on 2006-02-14
No KDE wizard i am, but try replacing sudo with kdesu. Should work. 
IH

---

