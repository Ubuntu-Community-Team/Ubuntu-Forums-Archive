---
title: "multi-user remote access"
date: 2011-03-15
forum: General Help
---

### Post by agent_509 on 2011-03-15
I've tried to find the solution to this but I haven't found quite what I'm looking for. I'm wondering if there's a way so that several people can log onto my computer at the same time. When they connect it goes to the login screen and they choose their account and log in. Everybody has a different account and sees a different desktop. Is that possible?

---

### Post by JRV on 2011-03-15
I use XDMCP on a local network.  It is not recommended for use over the internet.
For Ubuntu 9.04 and before you can enable it through the GUI.
It is not available in 10.10 and I think it will be in 11.04.

For over the internet use SSH. 

To enable XDMCP server for Ubuntu 9.10 and 10.04: 
```

   sudo gedit /etc/gdm/custom.conf

```

Add the following lines:
```

[xdmcp]
Enable=true
MaxPending=4
MaxSessions=16
MaxWait=15

```

Then, restart gdm with the command:
```

   sudo /etc/init.d/gdm restart

```

or reboot the PC.


On the client side there are two clients available, Xnest and Xephyr. I prefer Xephyr.
It installs with the command:
```

   sudo apt-get install xserver-xephyr

```

XDMCP will then be available after login from the command line, I use:
```

 Xephyr :1 -query HOSTNAME -fullscreen -once

```

If you need an XDMCP thin client let me know, I have instructions to create Ubuntu and Puppy based XDMCP thin clients.

---

### Post by HermanAB on 2011-03-15
You can use SSH to do that.  Install ssh-server and then each person can log in with:
$ ssh -X -C -c blowfish user@server "gnome-panel"

That works from Windows too, if you install Cygwin.

---

### Post by bodhi.zazen on 2011-03-15
> **HermanAB said:**
> That works from Windows too, if you install Cygwin.

FYI you do not need cygwin. You can use putty to connect and then use Xming as an X server.

[http://www.straightrunning.com/XmingNotes/](http://www.straightrunning.com/XmingNotes/)

The only reason I mention this is that putty / xming are portable.

---

