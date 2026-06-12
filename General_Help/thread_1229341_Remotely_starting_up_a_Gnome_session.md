---
title: "Remotely starting up a Gnome session"
date: 2009-08-02
forum: General Help
---

### Post by fuubaa on 2009-08-02
Hi,

Sorry if my terminology etc is a bit off, I hope what I'm asking is still clear enough...

I've set up TightVNC successfully (On Ubuntu 8). I can get access to it via SSH so can run commands remotely. 

I've found out how to enable remote desktop via the command line, so I'm half way there... 

[http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line](http://www.samlesher.com/ubuntu/ubuntu-704-enabledisable-remote-desktop-from-the-command-line)

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

But more often than not I forget to leave it logged in so when I'm out and about can't access it using VNC because according to the website:

[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

"Remote Desktop will only work if there&#8217;s a GNOME login session".

So is there a way of doing that remotely using the command line?

Thanks

---

### Post by XCan on 2009-08-02
I think the easiest is for you to simply start up vino (VNC server) whenever GDM comes up. You can easily do it by editing /etc/gdm/Init/Default . Add ```
 /usr/lib/vino/vino-server &
``` just before ```
 exit 0 
```. This way vino will start whenever the login screen comes up.

CAUTION: You will be kicked out when you login, but you can simply just reconnect to the server as your user will run its own vino-server. However, if you choose to disable the 'kicking out', you better setup vnc passwords for root. Come to think of it, you better setup vnc password for root either way using
```
 sudo vino-preferences 
```

---

