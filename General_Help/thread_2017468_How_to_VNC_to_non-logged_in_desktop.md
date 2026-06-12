---
title: "How to VNC to non-logged in desktop"
date: 2012-07-05
forum: General Help
---

### Post by savanna on 2012-07-05
I've been remotely upgrading a machine. All seems to have gone well, but I just want to check that the GUI is working.

In the past I've had the machine setup the machine so I can just VNC through an ssh tunnel when the user is (automatically) logged on.

```
ssh -f -L 5900:localhost:5900 foo@bar.dyndns.org \
x11vnc -safer -usepw -localhost -once -noxdamage \
-nowf -ncache 0 -scale 2/3 -display :0
```

But after the upgrade the user isn't being automatically logged on, so I was trying to VNC to the display manager, but no joy:

```
# ps -ef | grep auth
/usr/bin/X :0 -auth /var/run/lightdm/root/:0 \
-nolisten tcp vt7 -novtswitch -background none

```

This shows that the auth cookie is under /var/run/..., so I tried:

```
ssh -f -L 5900:localhost:5900 foo@bar.dyndns.org \
x11vnc -safer -usepw -localhost -once -noxdamage \
-nowf -ncache 0 -scale 2/3 -display :0 \
-auth /var/run/lightdm/root/:0

```

Any ideas on how to connect?

How would I disable the -nolisten in the X startup?

---

### Post by {CGL}ToWeR on 2012-07-16
Hi Sonia
I too would like to know how to the answer to this - I think there's a permissions issue with xauthority, and the auth file location too possibly..

As for disabling -nolisten, ie enabling listening you no need edit /etc/lightdm/lightdm.conf and add
[SeatDefaults]
...
xserver-allow-tcp=true

then
sudo service lightdm restart

You'll notice the option is gone in the process listing.
HTH

---

