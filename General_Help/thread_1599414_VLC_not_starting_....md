---
title: "VLC not starting ..."
date: 2010-10-17
forum: General Help
---

### Post by bkpa2med on 2010-10-17
I tried removing it and installing again but I still get the same code in the terminal:

[PHP]VLC media player 1.1.4 The Luggage (revision exported)
[0x85da284] main interface: creating httpd
[0x85da284] main interface error: socket bind error (Permission denied)
[0x85da284] main interface error: socket bind error (Permission denied)
[0x85da284] main interface error: cannot create socket(s) for HTTP host
[0x85da284] oldhttp interface error: cannot listen on :8080
[0x85da284] main interface error: no suitable interface module
Blocked: call to unsetenv("DBUS_ACTIVATION_ADDRESS")
Blocked: call to unsetenv("DBUS_ACTIVATION_BUS_TYPE")
[0x85db054] main interface: creating httpd
[0x85db054] main interface error: socket bind error (Permission denied)
[0x85db054] main interface error: socket bind error (Permission denied)
[0x85db054] main interface error: cannot create socket(s) for HTTP host
[0x85db054] oldhttp interface error: cannot listen on :8080
[0x85db054] main interface error: no suitable interface module
[0x8542914] main libvlc error: interface "default" initialization failed
[/PHP]

Any suggestions on how to fix this?

---

### Post by mc4man on 2010-10-17
If your intention is to vlc w/ the normal interface then this will open and reset 
```
vlc -I qt4 --reset-config
```

If you are trying to use the http interface then it's not set up correctly and or  possibly you'd need to run vlc as root (never used here..

---

### Post by bkpa2med on 2010-10-17
Thanks alot! I was trying to set up the remote for my iPhone. Guess something went wrong.

---

### Post by bkpa2med on 2010-10-18
You know by any chance how to set up the remote with VLC?

---

