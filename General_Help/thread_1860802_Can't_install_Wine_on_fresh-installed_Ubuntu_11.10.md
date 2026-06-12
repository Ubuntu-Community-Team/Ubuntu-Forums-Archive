---
title: "Can't install Wine on fresh-installed Ubuntu 11.10"
date: 2011-10-15
forum: General Help
---

### Post by JesusM on 2011-10-15
Hi!

I'm running a freshly installed Ubuntu 11.10. 

I try to install wine but I get this message:

```
The following packages have unmet dependencies:

wine1.3: PreDepends: dpkg (>= 1.14.12ubuntu3) but 1.16.0.3ubuntu5 is to be installed
         Depends: libc6 (>= 2.11) but 2.13-20ubuntu5 is to be installed
         Depends: libgettextpo0 but it is not going to be installed
         Depends: libglib2.0-0 (>= 2.12.0) but 2.30.0-0ubuntu4 is to be installed
         Depends: libgphoto2-2 (>= 2.4.10.1) but 2.4.11-3 is to be installed
         Depends: libgphoto2-port0 (>= 2.4.10.1) but 2.4.11-3 is to be installed
         Depends: liblcms1 (>= 1.15-1) but 1.19.dfsg-1ubuntu2 is to be installed
         Depends: libldap-2.4-2 (>= 2.4.7) but 2.4.25-1.1ubuntu4 is to be installed
         Depends: libmpg123-0 (>= 1.6.2) but it is not going to be installed
         Depends: libopenal1 but it is not going to be installed
         Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-4 is to be installed
         Depends: zlib1g (>= 1:1.1.4) but 1:1.2.3.4.dfsg-3ubuntu3 is to be installed
```Any idea? Am I doing anything bad?

Thanks

---

SOLVED:

the problem was with teh 'Server in Spain' at 'Software Sources'. once I've selected 'Main Server' everything is working fine.

thanks

---

### Post by westie457 on 2011-10-15
Hello and welcome to the Forums.

Did you try Wine from the Software Centre? or did you download from Wine HQ.

If the latter I suggest you try from the SC as it should be stable.
Another thing to try is PlayOnLinux also from the SC.

Play On Linux is the 'front-end' to Wine.

---

### Post by dino99 on 2011-10-15
the "natty" ppa works, the "oneiric" ppa dont due to missing ttf... package (change it into synaptic tab, or into /etc/apt/sources.list)

---

### Post by JesusM on 2011-10-15
Both. From the software center and from the WineHW Web Site. Both cases gave me same message.

And about PlayOnLinux ... if it is a FrontEnd I'd also need Wine, right?

Thanks anyway

---

### Post by westie457 on 2011-10-15
> **JesusM said:**
> Both. From the software center and from the WineHW Web Site. Both cases gave me same message.

And about PlayOnLinux ... if it is a FrontEnd I'd also need Wine, right?

Thanks anyway

Play on Linux installs Wine at the same time. However dyno99 has better advice than me. Try his suggestions first.

---

### Post by JesusM on 2011-10-15
> **dino99 said:**
> the "natty" ppa works, the "oneiric" ppa dont due to missing ttf... package (change it into synaptic tab, or into /etc/apt/sources.list)

And ... how should I do that?

Sorry, I am newbie on this

---

