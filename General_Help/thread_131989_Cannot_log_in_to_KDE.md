---
title: "Cannot log in to KDE"
date: 2006-02-17
forum: General Help
---

### Post by eqisow on 2006-02-17
Whenever I try to log in to my KDE desktop something quite intriguing happens. When I attempt to login it goes black as if it's about to boot into KDM... then goes right back to the login screen. This happens no matter who I log in as. 

If I ctrl+alt+F1 to the command line I am able to log in. If I then issue the stop command for KDM, followed by the start command, it takes me back to the login screen. The only difference is that under switch users it shows me loged on twice. if I switch it just takes me back to the command line. Under session it shows nothing selected, I'm not sure if this is normal or not. If I select a KDE session and then attempt to login the same thing happens, and it reverts back to no selection under session.

Am very confused. :(

---

### Post by aysiu on 2006-02-17
Have you tried this? ```
sudo /etc/init.d/kdm restart
```

---

### Post by eqisow on 2006-02-17
Yes, it brings the log in screen back up... at which point I still can't log in. :\

If I boot into command line mode and run 'startx' I get the following error:

```
/etc/X11/xinit/xinitrc: line9: /etc/X11/Xsession: No such file or directory
```

---

### Post by eqisow on 2006-02-17
OK, so I tried making an empty file at /etc/X11/Xsession. The error message regarding that file no longer shows up. I now get the following:

```
Couldn't open RGB_DB '/usr/X11R6/lib/X11/rgb'
```

---

### Post by eqisow on 2006-02-17
Some more, hopefuly helpful, info:

The file /etc/X11/xinit/xinitrc is as follows:

```
#!/bin/sh
#$Xorg:xinitrx.cpp,v 1.3 2000/08/17
#/etc/X11/xinit/xinitrx
#
#global xinitrc file, used by all X sessions started by xinit (startx)
#invoke global Xsession script
./etc/X11/Xsession
```

The output of slocate Xsession is:

```
/etc/X11/Xsession (the one I created)
/etc/X11/Xsession.options
/etc/X11/Xsession.d
/etc/X11/Xsession.d/30xorg-common_xresources
/etc/X11/Xsession.d/50xorg-common_determine-startup
/etc/X11/Xsession.d/90xorg-common_ssh-agent
/etc/X11/Xsession.d/99xorg-common_start
/etc/X11/Xsession.d/20xorg-common_process-args
/etc/kde3/kdm/Xsession
/usr/share/man/man5/Xsession.5.gz
/usr/share/man/man5/Xsession.options.5.gz
```

I tried using cp to move the Xsession file at /etc/kde3/kdm/Xsession to /etc/X11/Xsession. X will now start but only goes to a gray screen with an X for a curser.

---

