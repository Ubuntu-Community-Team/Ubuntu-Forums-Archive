---
title: "NX Client for Windows silently gets closed after connection"
date: 2009-12-19
forum: General Help
---

### Post by donald128 on 2009-12-19
Hey!
I connect remotely to my Ubuntu server from Vista machine.
Now I need to run a GUI application on the server (Wireshark).
So I decided to use FreeNX server/client to view Ubuntu GUI on Vista

I have successfully installed FreeNX on Ubuntu and NX Client on Vista.
I was following this guide
[https://help.ubuntu.com/community/FreeNX#Using%20custom%20SSH%20keys](https://help.ubuntu.com/community/FreeNX#Using%20custom%20SSH%20keys)

Unfortunately, now I found myself stuck with the following problem.

At the client, the !M logo window appears, but after a few seconds that window just closes, even without showing any error message.

Guys, I'm really stuck, please help!
Maybe I should have installed some graphical environment on the server?



These are the details from NX client, it seems there are no errors.

-----------------

Info: Display running with pid '7768' and handler '0x670d24'.

NXPROXY - Version 3.4.0

Copyright (C) 2001, 2007 NoMachine.
See [http://www.nomachine.com/](http://www.nomachine.com/) for more information.

Info: Proxy running in client mode with pid '2168'.
Session: Starting session at 'Sat Dec 19 10:58:35 2009'.
Warning: Connected to remote version 3.3.0 with local version 3.4.0.
Info: Connection with remote proxy completed.
Info: Using WAN link parameters 768/24/1/0.
Info: Using cache parameters 4/4096KB/16384KB/16384KB.
Info: Using pack method 'adaptive-9' with session 'kde'.
Info: Using ZLIB data compression 1/1/32.
Info: Using ZLIB stream compression 1/1.
Info: No suitable cache file found.
Info: Forwarding X11 connections to display ':0'.
Info: Listening to font server connections on port '11000'.
Session: Session started at 'Sat Dec 19 10:58:35 2009'.
Info: Established X server connection.
Info: Using shared memory parameters 0/0K.
Session: Terminating session at 'Sat Dec 19 10:58:37 2009'.
Session: Session terminated at 'Sat Dec 19 10:58:37 2009'.
-----------

---

