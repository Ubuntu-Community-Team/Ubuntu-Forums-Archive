---
title: "xnest problem - blinking screen but no login"
date: 2006-03-05
forum: General Help
---

### Post by KermitJr on 2006-03-05
Hi all,

Ok, I'm trying to do a little kdmrc remote access and by using Xnest.

I have XDMCP=true and in Xaccess uncommented *

Without the above done, I get the standard gray screen with an X.  When I do the above, I now get a window that flashes with white but no login or anything useful.

Edit: a bit more info.

I get the flashy screen from any box trying to access the machine.  I tried ifdown eth0 and -query localhost and get:

> Fatal server error:
XDMCP fatal error: Session declined. No valid address.

If I bring eth0 back up and try again (localhost), same flashy screen.

Please help.

KJ

---

### Post by KermitJr on 2006-03-07
No help? This may be a first.

I'm trying a few things still, but it doesn't work on any of my machines.

I thought it may be a hosts.allow issue, so I added the line:

ALL: 192.168.1.*

rebooted but still gray screen with black X and flashes white.

I know KDM is listening on 177 (followed LTSP troubleshooting stuff).

This is REALLY bugging me so please help!!!!

Thanks in advance.
KJ

---

### Post by KermitJr on 2006-03-07
OK, working some more on this:

I can do:


Xnest :1 -ac

and I get grey screen with X.  I can then type (in diff terminal) :    xterm -display :1
and it opens an xterm in the xnest window.  So the issue seems to be kdm not bringing up a display login with Xnest like it should.

HELP!!!

THanks,
KJ

---

### Post by patrixl on 2006-03-07
You need to upgrade to KDE 3.5.1, or use wdm if you're not yet willing to upgrade (xdm has the same trouble as kdm in Breezy, and I haven't tried gdm).

---

### Post by KermitJr on 2006-03-07
After two days, I finally got it to work.

I opened synaptic and did "Complete removal" of:

kdm
kdebase-bin

Then:
```
apt-get install kubuntu-desktop
```
This uninstalled and re-installed a large amount of programs and one prompted to overwrite the kdmrc file with an updated one.  I said yes and continued.

At the end end, I edited ```
/etc/kde3/kdm/kdmrc
``` to ```
[Xdmcp] enable=true
``` and restarted kdm via: ```
sudo /etc/init.d/kdm restart
```
Voila! now  ```
Xnest -query localhost :1
``` gives me a kdm login screen.

I'm not sure why simply trying to update didn't rewrite that kdmrc file, but the newer version is significantly different from the older version.

(PS: Don't forget to change the /etc/kde3/kdm/Xaccess file line #*     to *   )

---

### Post by amr2205 on 2007-12-07
Wooooow! Thank you very much, it works! =D>

---

