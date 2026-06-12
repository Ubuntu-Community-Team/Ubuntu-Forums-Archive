---
title: "error in compiling amarok 1.4"
date: 2009-10-13
forum: General Help
---

### Post by sarin_cv on 2009-10-13
Hi... I am getting the following error when running ./configure 
./configure --prefix=/usr --without-arts

checking for taglib >= 1.5... checking for taglib >= 1.4... Package taglib was not found in the pkg-config search path. Perhaps you should add the directory containing `taglib.pc' to the PKG_CONFIG_PATH environment variable No package 'taglib' found
configure: error: Library requirements (taglib >= 1.4) not met; consider adjusting the PKG_CONFIG_PATH environment variable if your libraries are in a nonstandard prefix so pkg-config can find them.

in synaptic, a package libtag1C2a is already installed. 
I have taken the source from the path [http://mirror.cc.columbia.edu/pub/software/kde/stable/amarok/](http://mirror.cc.columbia.edu/pub/software/kde/stable/amarok/)

plz help...

---

### Post by jmszr on 2009-10-13
sarin_cv,

I can't help you with your compiling situation, but if you want Amarok 1.4 try this:[http://ubuntumanual.org/posts/232/get-amarok-1-4-back-in-ubuntu-jaunty-9-04](http://ubuntumanual.org/posts/232/get-amarok-1-4-back-in-ubuntu-jaunty-9-04)

---

### Post by sarin_cv on 2009-10-13
hi...installed Amarok1.4 successfully... but later I found a comment in that page like, 

Don't install software from unknown sources, chances are they inserted some malicious code,

---

### Post by ramjet_1953 on 2009-10-13
Is there a particular reason why you feel the need to compile Amarok 1.4?

Amarok is available in Synaptic package manager, or you can just type in a terminal:

```
sudo apt-get install amarok
```

I use Hardy and the version in the repositories for me is 2:1.4.9.1

If you go to the Amarok website they have 2.2 available as a Debian download.

I believe that 2.2 will be standard in Kharmic.

Regards,
Roger :)

---

### Post by sarin_cv on 2009-10-14
the new version of amarok does not have any equalizer associated with it... in the old version there is provision to change engine... equlaizer is available with xine engine...

---

### Post by sarin_cv on 2009-10-26
> **sarin_cv said:**
> hi...installed Amarok1.4 successfully... but later I found a comment in that page like, 

Don't install software from unknown sources, chances are they inserted some malicious code,

Any comment on this???

---

