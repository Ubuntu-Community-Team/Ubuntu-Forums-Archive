---
title: "startx error"
date: 2006-03-09
forum: General Help
---

### Post by bseck on 2006-03-09
Hi - I have recently installed Breezy Badger 5.10 and all went fine. Now I'm connecting to my server using putty/ssh. 

What I can't do is **startx **- currently using gnome. I get the following error:

[COLOR="Red"][FONT="Courier New"]~$ startx
xauth:  creating new authority file /home/bseck/.serverauth.9733
Fatal server error:
Server is already active for display 0
        If this server is no longer running, remove /tmp/.X0-lock
        and start again.
Please consult the The X.Org Foundation support
         at [http://wiki.X.Org](http://wiki.X.Org)
 for help.
Couldnt get a file descriptor referring to the console[/FONT][/COLOR]


I have been searching in the forum but couldn't see a clear solution for my problem.

Thanks in advance for your help.

-Barra

---

### Post by taurus on 2006-03-09
When Ubuntu boots up, do you see a GUI login screen???  If it drops you to a terminal then try removing "/tmp/.X0-lock" as said in the error message...
```

sudo rm /tmp/.X0-lock
startx

```

---

### Post by bseck on 2006-03-09
Hi -

To start, this is the closest I've been to a solution.

Yes, I do see a GUI login when it boots. I removed the lock file and this is what happened.

**case#1**: I have an x session opened on the actual server. startx fails with the error:

[COLOR="DarkRed"]bash(7772): libnotify: Error connecting to session bus: Unable to determine the address of the message bus.

On the server side the error is: "detected a panel is already running and will now exit". 
[/COLOR]

So i decided to add my display in my .xinitrc and it worked. 

**case#2**: I don't have an active x session on the actual server.
The new session displays on the server unless i set the display in the .xinitrc.

- Does all this make sense?
- am I missing something else?

By the way, i didn't get a login screen. Is it because i'm already authenticated via ssh?

Thanks

Barra

---

