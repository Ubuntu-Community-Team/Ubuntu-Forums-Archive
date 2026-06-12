---
title: "Remote Desktop issues"
date: 2009-11-17
forum: General Help
---

### Post by doctorbighands on 2009-11-17
Problem: I rebooted my headless home server, and now it won't let me access it via Remote Desktop Viewer.

Details: I haven't installed any updates recently, so it can't be that. I can still SSH and FTP into the server, and it is still serving my website properly - Remote Desktop seems to be the only problem. Port 5900 is open on my router, so no issue there. The server is running Ubuntu server edition with XFCE installed on top of it (because I'm still n00b enough to need a GUI for some things). I've tried logging in using Remote Desktop Viewer in Ubuntu, as well as VNCViewer in Windows, and neither will let me in. I have tried to reboot an additional two times, getting the same negative result each time.

I have no idea what happened. If any of you kind folks out there can help me get my access back, I would be eternally grateful.

Thank you!

---

### Post by P4man on 2009-11-18
I think the problem is that headless it wont boot into a gui because it cant detect the monitor. Perhaps this will help:
[http://ubuntuforums.org/showthread.php?t=825384](http://ubuntuforums.org/showthread.php?t=825384)

---

### Post by doctorbighands on 2009-11-18
The thing is, though, I have it set to boot into X when the machine starts up, and login automatically. With previous reboots, this has never been an issue.

Just to test the theory, I logged in via SSH in the terminal and typed "sudo startx" and received a reply of "the X server is already running." Hmmmm...

Any other ideas?

---

### Post by HermanAB on 2009-11-18
Well, since it is a server and you have SSH running, just do this:
$ ssh -X -c blowfish -C user@ipaddressofserver gnome-panel

On a Linux system, VNC is almost always the *wrong* solution...

Cheers,

Herman

---

### Post by XCan on 2009-11-18
On a Linux server probably, but for an office workstation, VNC is handy indeed. Although the OP is apparently running a server, thus I agree with HermanAB.

---

### Post by sefs on 2009-11-18
This may be a long shot but you can log in with ssh and ..

```

sudo /etc/init.d/gdm restart

```

give it some seconds and try to vnc in...

or

```

sudo /etc/init.d/gdm restart
startx

```

and try to vnc in.

While you are sshed in checy your /etc/xinetd.d/Xvnc file

find this line ...

```

	server_args = -inetd :1 -query 127.0.0.1 -geometry 1024x768 -depth 16 -once -fp /usr/share/fonts/X11/misc -DisconnectClients=0 -NeverShared passwordFile=/root/.vncpasswd -extension XFIXES

```

and make sure it ahs 127.0.0.1 as above and not localhost

---

### Post by doctorbighands on 2009-11-19
> **HermanAB said:**
> Well, since it is a server and you have SSH running, just do this:
$ ssh -X -c blowfish -C user@ipaddressofserver gnome-panel

On a Linux system, VNC is almost always the *wrong* solution...

Cheers,

Herman

Tried this, and got the following response:

```

/usr/bin/X11/xauth:  error in locking authority file /home/nick/.Xauthority
X11 connection rejected because of wrong authentication.
Cannot open display: 
Run 'gnome-panel --help' to see a full list of available command line options.

```

I have no idea what this means.

---

