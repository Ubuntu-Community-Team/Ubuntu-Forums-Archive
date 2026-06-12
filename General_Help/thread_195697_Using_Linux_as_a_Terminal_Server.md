---
title: "Using Linux as a Terminal Server"
date: 2006-06-13
forum: General Help
---

### Post by jethro10 on 2006-06-13
Hi,
the title is about right.
On any of my Windows servers, even if they are NOT logged on. I can run a Remote desktop using RDP, log on, do my suff, and log out again.

Best i've go so far with Ubuntu is running VNC, but the Ubuntu box needs to be logged on unlike windows and I take over the current desktop, which is a bummer IF someone is using it.
Is there a package that alows me to remotley log onto an Ubuntu server that is not already logged on and take a new session if the server is in-use by someone.

Think i've just described a terminal server?

Jeff

---

### Post by AndyCooll on 2006-06-13
You could enable XDMCP

Or another alternative is to install Freenx.

Both in effect let you begin a "session" on a remote pc.

:cool:

---

### Post by jethro10 on 2006-06-13
[QUOTE=AndyCooll]You could enable XDMCP

Or another alternative is to install Freenx.

Both in effect let you begin a "session" on a remote pc.

:cool:[/QUOTE]

Thanks.
XDMCP look hard to set-up and it seems advised no to do it for security reasons.

Freenx needs the commercial download of Nx which has the free stuff in it so thats fine. But a dependency fails that is actually installed!

Plan B: Give up.
Jeff

---

### Post by charnov on 2006-06-13
[Deleted] I didn't read all the way through....my bad

---

### Post by volksman on 2006-06-14
FreeNX works when if you install it as per [http://ubuntuforums.org/showthread.php?t=156019&highlight=freenx](http://ubuntuforums.org/showthread.php?t=156019&highlight=freenx)

only problem I have is if I have a desktop in session on the machine and I use NX remotely to access that machine it creates a new session not join the existing.  In M$ world I believe this is refered to as connecting to console.  Anyone know how to make that happen with NX?

---

### Post by jethro10 on 2006-06-16
[QUOTE=volksman]FreeNX works when if you install it as per [http://ubuntuforums.org/showthread.php?t=156019&highlight=freenx](http://ubuntuforums.org/showthread.php?t=156019&highlight=freenx)

only problem I have is if I have a desktop in session on the machine and I use NX remotely to access that machine it creates a new session not join the existing.  In M$ world I believe this is refered to as connecting to console.  Anyone know how to make that happen with NX?[/QUOTE]

Will try that now

---

### Post by AndyCooll on 2006-06-16
XDMCP doesn't need any installation at all it simply requires you to make a change to the "Login Window" settings. As for security, it depends on how your firewall is set up. All my pc's are behind my routers firewall so it isn't really a problem for my homw network.

Freenx can potentially be installed via Synaptic, not sure which repository it's in though, that's what I used to do when I used it (I now prefer XDMCP). Then just do a search for "nx" and install freenx, client, server etc.

:cool:

---

### Post by garyng on 2006-06-16
xdmcp is only good for private network but is otherwise quite simple to setup, just enable it in GDM/KDM. But you don't have sound and it also need quite some bandwidth and it is not safe through public network.

You can also setup VNC service so you don't need to logon(in combination of XDMCP) and would see the GDM logon screen in your VNC viewer instead. This is better in terms of bandwidth than XDMCP but like it is not safe through public network.

freenx is the closest to TS, yet pale in easy of use and configuration. It is safe, have sound and the suspend/resume feature(though quite iffy).

---

### Post by rvergara on 2006-06-16
[QUOTE=garyng]

freenx is the closest to TS, yet pale in easy of use and configuration. It is safe, have sound and the suspend/resume feature(though quite iffy).[/QUOTE]

I use both Freenx and TS on a daily basis. Although TS is easy to configure, Freenx has way better performance. Local printing is better supported in Freenx as well.

Ramiro

---

