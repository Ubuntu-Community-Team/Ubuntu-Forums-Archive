---
title: "can't get 2nd user to work on freenx"
date: 2010-02-19
forum: General Help
---

### Post by prickly on 2010-02-19
I have successfully installed FreeNX on Ubuntu Desktop (Karmic) and can access FreeNX with the user that set it up. 

I then added a second user - and they get most of the way through the connection before it fails (I see the big red letters on the screen and then it fails).

I have edited /etc/nxserver/node.conf and uncommented ENABLE_PASSDB_AUTHENTICATION and set its value to "1".

I have also added the second user to FreeNX: sudo nxserver --adduser *user*

I have also followed the troubleshooting instruction [here]("https://help.ubuntu.com/community/FreeNX") as follows (for the 2nd users home folder):

```
sudo rm .Xauthority
sudo touch Xauthority
sudo chmod 600 Xauthority
```

None of my troubleshooting has made any difference yet. 

Can anyone point me in the right direction?

Many thanks!

EDIT: This is the ourput from FreeNX:

Info: Proxy running in client mode with pid '1176'.
Session: Starting session at 'Thu Feb 18 21:09:23 2010'.
Warning: Connected to remote version 3.2.0 with local version 3.4.0.
Info: Connection with remote proxy completed.
Info: Using LAN link parameters 1536/24/1/0.
Info: Using pack method 'adaptive-9' with session 'kde'.
Info: Not using NX delta compression.
Info: Not using ZLIB data compression.
Info: Not using ZLIB stream compression.
Info: Not using a persistent cache.
Info: Forwarding X11 connections to display ':0'.
Info: Forwarding multimedia connections to port '6000'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Thu Feb 18 21:09:23 2010'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Thu Feb 18 21:09:24 2010'.
Session: Session terminated at 'Thu Feb 18 21:09:24 2010'.

---

