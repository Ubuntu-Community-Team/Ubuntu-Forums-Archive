---
title: "Draftsight needs dependancy from i386"
date: 2011-04-22
forum: General Help
---

### Post by billiard on 2011-04-22
Hey, I am new to Linux but I have learned a lot already from using the terminal. I am trying to install 32 bit DraftSight onto the 64 bit ubuntu (Yes DraftSight currently only has a 32 bit program). I install[COLOR=Black]ed libaudio2, libdirectfb-extra, and libxcb-render-util0 just as this website said to do: [http://courira.ca/en/2011/03/draftsight-for-linux-how-to-install-on-ubuntu-64-bit](http://courira.ca/en/2011/03/draftsight-for-linux-how-to-install-on-ubuntu-64-bit) . The problem is that after I run the command:
[/COLOR]```

sudo dpkg -i --force-all ~/Downloads/DraftSight.deb

```it returns the following:[COLOR=Black]
[/COLOR]```

Unpacking replacement dassault-systemes-draftsight:i386 ...
dpkg: dependency problems prevent configuration of dassault-systemes-draftsight:i386:
 dassault-systemes-draftsight:i386 depends on libexpat1 (>= 2.0.1-4).
 dassault-systemes-draftsight:i386 depends on libglib2.0-0 (>= 2.22.3-0).
 dassault-systemes-draftsight:i386 depends on libpcre3 (>= 7.8-3).
 dassault-systemes-draftsight:i386 depends on libselinux1 (>= 2.0.85-2).
 dassault-systemes-draftsight:i386 depends on zlib1g (>= 1:1.2.3.3.dfsg-13).
 dassault-systemes-draftsight:i386 depends on libc6 (>= 2.10.1-0).
 dassault-systemes-draftsight:i386 depends on libx11-6 (>= 2:1.2.2-1).
 dassault-systemes-draftsight:i386 depends on libxau6 (>= 1:1.0.4-2).
 dassault-systemes-draftsight:i386 depends on libxcomposite1 (>= 1:0.4.0-4).
 dassault-systemes-draftsight:i386 depends on libxcursor1 (>= 1:1.1.9-1build1).
 dassault-systemes-draftsight:i386 depends on libxdamage1 (>= 1:1.1.1-4).
 dassault-systemes-draftsight:i386 depends on libxdmcp6 (>= 1:1.0.2-3).
 dassault-systemes-draftsight:i386 depends on libxext6 (>= 2:1.0.99.1-0).
 dassault-systemes-draftsight:i386 depends on libxfixes3 (>= 1:4.0.3-2build1).
 dassault-systemes-draftsight:i386 depends on libxi6 (>= 2:1.2.1-2).
 dassault-systemes-draftsight:i386 depends on libxinerama1 (>= 2:1.0.3-2).
 dassault-systemes-draftsight:i386 depends on libxrandr2 (>= 2:1.3.0-2).
 dassault-systemes-draftsight:i386 depends on libxrender1 (>= 1:0.9.4-2).
 dassault-systemes-draftsight:i386 depends on libatk1.0-0 (>= 1.28.0-0).
 dassault-systemes-draftsight:i386 depends on libcairo2 (>= 1.8.8-2).
 dassault-systemes-draftsight:i386 depends on libdirectfb-extra (>= 1.2.7-2).
 dassault-systemes-draftsight:i386 depends on libfontconfig1 (>= 2.6.0-1).
 dassault-systemes-draftsight:i386 depends on libfreetype6 (>= 2.3.9-5).
 dassault-systemes-draftsight:i386 depends on libgtk2.0-0 (>= 2.18.3-1).
 dassault-systemes-draftsight:i386 depends on libpango1.0-0 (>= 1.26.0-1).
 dassault-systemes-draftsight:i386 depends on libpixman-1-0 (>= 0.14.0-1).
 dassault-systemes-draftsight:i386 depends on libpng12-0 (>= 1.2.37-1).
 dassault-systemes-draftsight:i386 depends on libxcb-render-util0 (>= 0.3.6-1).
 dassault-systemes-draftsight:i386 depends on libxcb-render0 (>= 1.4-1).
 dassault-systemes-draftsight:i386 depends on libxcb1 (>= 1.4-1).
 dassault-systemes-draftsight:i386 depends on libcomerr2 (>= 1.41.9-1).
 dassault-systemes-draftsight:i386 depends on libdbus-1-3 (>= 1.2.16-0).
 dassault-systemes-draftsight:i386 depends on libexpat1 (>= 2.0.1-4).
 dassault-systemes-draftsight:i386 depends on libgcc1 (>= 1:4.4.1-4).
 dassault-systemes-draftsight:i386 depends on libgcrypt11 (>= 1.4.4-2).
 dassault-systemes-draftsight:i386 depends on libglib2.0-0 (>= 2.22.3-0).
 dassault-systemes-draftsight:i386 depends on libgpg-error0 (>= 1.6-1).
 dassault-systemes-draftsight:i386 depends on libkeyutils1 (>= 1.2-10).
 dassault-systemes-draftsight:i386 depends on libpcre3 (>= 7.8-3).
 dassault-systemes-draftsight:i386 depends on libuuid1 (>= 2.16-1).
 dassault-systemes-draftsight:i386 depends on zlib1g (>= 1:1.2.3.3.dfsg-13).
 dassault-systemes-draftsight:i386 depends on libc6 (>= 2.10.1-0).
 dassault-systemes-draftsight:i386 depends on libgl1-mesa-glx (>= 7.6.0-1).
 dassault-systemes-draftsight:i386 depends on libglu1-mesa (>= 7.6.0-1).
 dassault-systemes-draftsight:i386 depends on libice6 (>= 2:1.0.5-1).
 dassault-systemes-draftsight:i386 depends on libsm6 (>= 2:1.1.0-2).
 dassault-systemes-draftsight:i386 depends on libx11-6 (>= 2:1.2.2-1).
 dassault-systemes-draftsight:i386 depends on libxau6 (>= 1:1.0.4-2).
 dassault-systemes-draftsight:i386 depends on libxdamage1 (>= 1:1.1.1-4).
 dassault-systemes-draftsight:i386 depends on libxdmcp6 (>= 1:1.0.2-3).
 dassault-systemes-draftsight:i386 depends on libxext6 (>= 2:1.0.99.1-0).
 dassault-systemes-draftsight:i386 depends on libxfixes3 (>= 1:4.0.3-2build1).
 dassault-systemes-draftsight:i386 depends on libxrender1 (>= 1:0.9.4-2).
 dassault-systemes-draftsight:i386 depends on libxt6 (>= 1:1.0.5-3).
 dassault-systemes-draftsight:i386 depends on libxxf86vm1 (>= 1:1.0.2-1).
 dassault-systemes-draftsight:i386 depends on libaudio2 (>= 1.9.2-1).
 dassault-systemes-draftsight:i386 depends on libavahi-client3 (>= 0.6.25-1).
 dassault-systemes-draftsight:i386 depends on libavahi-common3 (>= 0.6.25-1).
 dassault-systemes-draftsight:i386 depends on libcups2 (>= 1.4.1-5).
 dassault-systemes-draftsight:i386 depends on libdrm2 (>= 2.4.14-1).
 dassault-systemes-draftsight:i386 depends on libfontconfig1 (>= 2.6.0-1).
 dassault-systemes-draftsight:i386 depends on libgnutls26 (>= 2.8.3-2).
 dassault-systemes-draftsight:i386 depends on libgssapi-krb5-2 (>= 1.7dfsg~beta3-1).
 dassault-systemes-draftsight:i386 depends on libk5crypto3 (>= 1.7dfsg~beta3-1).
 dassault-systemes-draftsight:i386 depends on libkrb5-3 (>= 1.7dfsg~beta3-1).
 dassault-systemes-draftsight:i386 depends on libkrb5support0 (>= 1.7dfsg~beta3-1).
 dassault-systemes-draftsight:i386 depends on libstdc++6 (>= 4.4.1-4).
 dassault-systemes-draftsight:i386 depends on libtasn1-3 (>= 2.2-1).
 dassault-systemes-draftsight:i386 depends on libxcb1 (>= 1.4-1).
dpkg: error processing dassault-systemes-draftsight:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 dassault-systemes-draftsight:i386

```I installed ia32-libs and getlibs. I tried using get libs to get one of these dependencies and it said I already had them.

Does anyone know how to get these dependencies or is a there some other fix?

thanks,
billiard

---

### Post by billiard on 2011-04-25
Bump

---

### Post by Redi46464 on 2011-04-29
Yeah, how can I install that on 64bit Ubuntu 11?
The ```
sudo dpkg -i --force-architecture DraftSight.deb
``` gives back that:
```
redi@TX2:~/Stažené$ sudo dpkg -i --force-architecture DraftSight.deb
dpkg: varování: potla&#269;uji problém, protože je nastaveno --force:
 architektura balíku (i386) se neshoduje se systémem (amd64)
dpkg: dívám se na DraftSight.deb obsahující dassault-systemes-draftsight:i386, p&#345;ed-závislostní problém:
 dassault-systemes-draftsight:i386 p&#345;ed-závisí na libexpat1 (>= 2.0.1-4)
dpkg: chyba p&#345;i zpracovávání DraftSight.deb (--install):
 p&#345;ed-závislostní problém - neinstaluji dassault-systemes-draftsight:i386
P&#345;i zpracování nastaly chyby:
 DraftSight.deb
redi@TX2:~/Stažené$ 

```Sorry for the Czech terminal :oops:

---

### Post by kadeck on 2012-11-07
bump

---

### Post by robert shearer on 2012-11-07
> **kadeck said:**
> bump
This thread is so old that you would be advised to start a completely **new thread** on this topic and supply as much information as possible eg Ubuntu version, system specs(ram, processor,graphics card etc), and anything you may have tried already to install the application.


[http://askubuntu.com/questions/176719/draftsight-for-ubuntu-12-04-lts-64bit](http://askubuntu.com/questions/176719/draftsight-for-ubuntu-12-04-lts-64bit)

---

### Post by wildmanne39 on 2012-11-07
Old thread closed.

---

