---
title: "How To Yahoo Messenger On Jaunty ?"
date: 2009-06-30
forum: General Help
---

### Post by stilling on 2009-06-30
sorry for disturb , i know about kopete , gyachi , gaim , pidgin ... etc etc
but let`s say that i whant old yahoo ugly messenger provided by yahoo and i whant to install i take the debian installer lib 0.9.6 installed to latest version but .....
Se despacheteaz&#259; ymessenger (din ymessenger.deb) ...
dpkg: probleme de dependen&#539;e preîntâmpin&#259; configurarea lui ymessenger:
 ymessenger depinde de **_[COLOR="Red"]libgdk-pixbuf2 (>= 0.13.0[/COLOR]_**); oricum:
  Pachetul [COLOR="Red"]**_libgdk-pixbuf2 not installed_**[/COLOR].
 ymessenger depinde de libgtk1.2 (>= 1.2.0); oricum:
  Pachetul [COLOR="Red"]**_libgtk1.2 not installed_**[/COLOR].
 ymessenger depinde de xlibs (>> 3.3.6); oricum:
  Pachetul [COLOR="Red"]**_xlibs not installed_**[/COLOR].
dpkg: eroare la procesarea ymessenger (--install):
 probleme de dependen&#539;e - l&#259;sat neconfigurat
Erori întâlnite în timpul prelucr&#259;rii:
 ymessenger
]

how to get this to work in my ubuntu jaunty please tell me only how to 

thanks very much in advance.!

---

### Post by abhi_69 on 2009-06-30
yahoo messanger for linux is very old & troublesome...its dependencies r so old version that, they r useless in now-a-days. so, u can't install it almost in any latest distro of linux (like-ubuntu 9.04).u can try pidgin or kopete. they r far more better than yahoo messanger for linux. u can also try yahoo messanger for web ([www.web.im](www.web.im)) or [www.meebo.com](www.meebo.com).
i use pidgin & it working for me very well with my yahoo account.
u can visit this thread for more info.
[http://ubuntuforums.org/showthread.php?t=81895](http://ubuntuforums.org/showthread.php?t=81895)
take care.

---

### Post by stilling on 2009-06-30
ok i resolved some problems my only problem now is how to install xlibs can you tell me that please and belive i know pidgin ... kopete gyachi is the best for the moment for yahoo but i whant to know now how to install xlibs in jaunty?

and thanks for your answer!

---

### Post by abhi_69 on 2009-06-30
> **stilling said:**
> ok i resolved some problems my only problem now is how to install xlibs can you tell me that please and belive i know pidgin ... kopete gyachi is the best for the moment for yahoo but i whant to know now how to install xlibs in jaunty?

and thanks for your answer!
what happened if u type-
$ sudo apt-get install xlibs
i think this will install xlibs (& dependencies of xlibs) for u.
do u try it?
thanz

---

### Post by stilling on 2009-06-30
it say that the package is or old or is disponible from another source
and it does not indicate what package contains that


thanks for the quiq reply

---

### Post by t0p on 2009-06-30
> **stilling said:**
> it say that the package is or old or is disponible from another source
and it does not indicate what package contains that


If the package is "old", that means it's ancient and is no longer available.  Which doesn't surprise me if this is happening when you are trying to install yahoo's linux messenger app.  That app is ancient and not worth bothering with.

If "disponible" means "available", the phrase "is disponible from another source" means it is available from another source.  So you need to fire up google and look for it.

Or you could just forget yahoo's messenger app and install something up to date.

---

### Post by stilling on 2009-06-30
Done i aborted the instalation for ymessenger ... i repaird my gyachi .... i was able to receive messages but not to write with gyachi 1.1.71 but i changed the server and no i connect thru cn.scs.yahoo.com .... and worcks just fine ..

10q all very much for the help

---

