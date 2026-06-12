---
title: "ServerInstall+kdebase+kdm does not equal happy face"
date: 2006-03-30
forum: General Help
---

### Post by AndEat on 2006-03-30
I am trying to install the ubuntu core, then the kdebase, and then kdm as a login manager, but I've got nothing. 

I was able to install both kdebase and kdm via the console but I'm left spinning my wheels as to configuring to NOT boot to a console and to the lovely GUI. 

I am just starting to unravel what needs to be done but I know that KDM must be configured somehow among a variety of other things I probably am unaware of at this point. 

Any help, tips, etc on getting an ubuntu server install to the KDE base with KDM login manager would be appreciated. 

thanks](*,)

---

### Post by ispmarin on 2006-03-30
Do your X starts when you type "startx"? If so, your X is working, the problem is just kdm. Go to /etc/X11 and create a file named default-display-manager, and inside put
/usr/bin/kdm.
This should start kdm when it boots. But, if startx does not put you X to work... the problem is X :mrgreen:

---

### Post by AndEat on 2006-04-15
[QUOTE=AndEat]I am trying to install the ubuntu core, then the kdebase, and then kdm as a login manager, but I've got nothing. 

I was able to install both kdebase and kdm via the console but I'm left spinning my wheels as to configuring to NOT boot to a console and to the lovely GUI. 

I am just starting to unravel what needs to be done but I know that KDM must be configured somehow among a variety of other things I probably am unaware of at this point. 

Any help, tips, etc on getting an ubuntu server install to the KDE base with KDM login manager would be appreciated. 

thanks](*,)[/QUOTE]


Well in case anybody is thrashing about with similar problems it has much to do with not installing X windows duh:???: ......installed the kde desktop package and had no problems but much more software to deal with...........

---

