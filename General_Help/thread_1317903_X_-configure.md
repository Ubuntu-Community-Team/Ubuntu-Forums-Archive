---
title: "X -configure"
date: 2009-11-07
forum: General Help
---

### Post by martolinacorsica on 2009-11-07
Hi I would like to change the depth of my screen to 32 bit, But I have no X11/xorg.conf file to edit. Apparently this is not needed in ubuntu, then I have tried to get one by typing 
sudo X -configure 
but I get this error message:
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional information.

 ddxSigGiveUp: Closing log

I then look at /var/log/Xorg.0.log and get again
_XSERVTransSocketUNIXCreateListener: ...SocketCreateListener() failed
_XSERVTransMakeAllCOTSServerListeners: server already running

Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already run
ning

Please consult the The X.Org Foundation support 
     at [http://wiki.x.org](http://wiki.x.org)
 for help. 
Please also check the log file at "/var/log/Xorg.0.log" for additional informati
on.

(WW) xf86CloseConsole: KDSETMODE failed: Bad file descriptor
(WW) xf86CloseConsole: VT_GETMODE failed: Bad file descriptor
(WW) xf86OpenConsole: VT_GETSTATE failed: Bad file descriptor
 ddxSigGiveUp: Closing log

Does anyone have an idea of what could I do?
:p

---

### Post by jocko on 2009-11-07
> **martolinacorsica said:**
> Fatal server error:
Cannot establish any listening sockets - Make sure an X server isn't already running

...

Does anyone have an idea of what could I do?
:p
Try to do what it tells you to. Stop the running x server:
```
sudo service gdm stop
```
Then login in the virtual terminal and run the command:
```
sudo X -configure
```

---

### Post by martolinacorsica on 2009-11-08
THanks!!
It worked, I could generate the new xorg.conf file, put it in the correct directory /etc/X11
and edit it. 
):P

---

