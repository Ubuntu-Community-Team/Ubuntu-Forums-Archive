---
title: "x11vnc autostart"
date: 2010-11-02
forum: General Help
---

### Post by otakon87 on 2010-11-02
Hi, i'm a newbie in the linux world.. I need to start the x11vncserver automatically every time i turn on the pc (autologin enabled), I noticed there is 'application autostart' in the session and startup menu. What should I write in the command line? I run it without password, ultravnc file transfer mode, port 5900.

thank you!

---

### Post by krunge on 2010-11-03
Maybe:
```

/usr/bin/x11vnc -ultrafilexfer -o /tmp/x11vnc.log -rfbport 5900

```
The '-o' is to capture a log file to help debugging getting this working. If you can't understand any error messages in the log file, then post it here.

If are going over the internet and want to know how to use encryption and a password with x11vnc just ask.

---

