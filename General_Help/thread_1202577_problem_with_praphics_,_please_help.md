---
title: "problem with praphics , please help"
date: 2009-07-02
forum: General Help
---

### Post by sudoomar on 2009-07-02
hello

i have ubuntu Jaunty..

i 've installed Matlab on it ..it worked fine...

the problem that today i tried to run matlab it started but with a grey screen..i had the same problem once but when i restarted the pc it prompted me an error screen saying that graphical settings are not good..it asked me if i want to adjust them

this time i could not do this..and i am getting this grey screen

---

### Post by Boondoklife on 2009-07-02
try `Xorg -configure` in a terminal, this should help you reconfigure it.

---

### Post by sudoomar on 2009-07-02
> **maletek said:**
> try `Xorg -configure` in a terminal, this should help you reconfigure it.

i get the following error

```
Fatal server error:
Server is already active for display 0
	If this server is no longer running, remove /tmp/.X0-lock
	and start again.


Please consult the The X.Org Foundation support 
	 at http://wiki.x.org
 for help. 

 ddxSigGiveUp: Closing log

```

---

### Post by sudoomar on 2009-07-02
any help please

---

### Post by TeoBigusGeekus on 2009-07-02
Reboot and choose recovery mode from grub.
There will be an option to reconfigure your graphic settings.

---

### Post by sudoomar on 2009-07-02
thanx very much..problem risolved

---

