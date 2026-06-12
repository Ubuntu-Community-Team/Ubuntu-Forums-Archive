---
title: "Xdmcp &amp; Gdm/kdm"
date: 2006-02-08
forum: General Help
---

### Post by edoardo on 2006-02-08
I tried for long (and reserached forums & the web at large) to get XDMCP working on my network of ubuntu 5.10 machines.
My findings:

xdmcp in kdm is BROKEN - no f****in way to get it to work 

xdmcp in gdm may work but for me:

-works locally in a nested window started as
  Xnest :1 -query localhost
or
  Xnest :1 -query machinename

-works from a remote machine running windows and cygwin/X
-does NOT work from a remote machine using Xnest or kde remote login,
in both cases i get the grey X background but no login UI

because cygwin works and native X don't on remote machine that may be my fault. I tried stopping firewalls but in any case they don't show rejected packets. So I'm at a loss ...

any help ?

---

### Post by oakz on 2006-02-08
Two things. First, by default the X server is configured to disallow (remote) TCP connections. To enable these connections, find the following line in /etc/gdm/gdm.conf and change "true" to "false":
DisallowTCP=true

Be aware that this opens a port to remote connections, a potential security risk, but if this is a private network that is probably not an issue.

Second, even if your X server will listen for remote connections, you need to configure which hosts are allowed to connect to it. See the "xhost" command for instructions on this. Two quick examples:

This will allow any remote host to connect to your X server, use with caution (again in a private network, not so big a deal):
$ xhost +

...or you can add a specific host using
$ xhost +<hostname>

Hope that helps.

---

### Post by edoardo on 2006-02-09
thanks oakz, still no joy.

---

### Post by dpm on 2006-02-16
Yeah, I've been trying to setup XDMCP login in my LAN following oakz' suggestions, but I'm also only getting a black background and the cross mouse cursor.

Any ideas anyone?

BTW, for those of you who do not like the command line, there's also the possibility of doing the following step
> Two things. First, by default the X server is configured to disallow (remote) TCP connections. To enable these connections, find the following line in /etc/gdm/gdm.conf and change "true" to "false":
DisallowTCP=true
from the GUI: System>Administration>Login Screen Setup>Security tab>"Deny TCP connections to Xserver" unchecked.

---

