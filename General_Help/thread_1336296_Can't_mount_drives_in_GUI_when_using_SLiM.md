---
title: "Can't mount drives in GUI when using SLiM"
date: 2009-11-24
forum: General Help
---

### Post by listerofsmeg1 on 2009-11-24
More issues with SLiM :(
Since switching to SLiM (installed from the jaunty repos) I've had a few issues.  Last one being no audio devices until I added my user to the "audio" group.

New issue: Clicking a drive to mount in Nautilus, or Places menu in xfce I get the following 2 errors:

"Rejected send message, 1 matched rules; type="method_call", sender=":1.55" (uid=1000 pid=2315 comm="exo-mount) interface="org.freedesktop.Hal.Device.Volume" member="Mount" error name="(unset)" requested_reply=0 destination="org.freedesktop.Hal" (uid=0 pid=1029 comm="hald))."

and 

"Not Authorized"

mounting from command line does work however, and if i switch back to GDM GUI mounting works.  Anyone know a way to fix this?

---

### Post by listerofsmeg1 on 2009-11-24
Ok I'm one step closer.  It's all something to do with the Xsession loading.
I changed /etc/slim.conf to use my .xinitrc file as the login command.
Original:  (which works fine)
```
login_cmd    exec /bin/bash -login /etc/X11/Xsession %session
```
Custom:   (which doesn't work)
```
login_cmd    exec /bin/bash -login ~/.xinitrc
```

I did it so that xfce would be the default instead of gnome.  How would I change /etc/X11/Xsession %session to make xfce the default.  Or get my xinitrc to load the session correctly?

contents of ~/.xinitrc:
```

Dsession=startxfce4

case $1 in
startxfce4)
	exec startxfce4
	;;
gnome-session)
	exec gnome-session
	;;
fluxbox)
	exec fluxbox
	;;
blackbox)
	exec fluxbox
	;;
*)
	exec $Dsession
	;;
esac
```

---

### Post by listerofsmeg1 on 2009-11-30
Just in case anyone else runs into this same issue I found the fix.  9.10 looks for ~/.xsession instead of ~/.xinitrc.  Changing that worked like a charm. :)

---

