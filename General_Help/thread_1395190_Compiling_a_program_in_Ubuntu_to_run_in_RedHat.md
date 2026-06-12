---
title: "Compiling a program in Ubuntu to run in RedHat"
date: 2010-01-31
forum: General Help
---

### Post by Kawaiii on 2010-01-31
Hi,
So I use my university's computers a lot, and I like being able to bring my data with me.  They use RedHat 5 32-bit.  I use windows a lot, so my passwords are stored in KeePass.  There's a *nix version called keepassx that I would like to be able to run on those computers. I can't get anything from repos on there.  But to compile it, I need the qt library, which isn't on those computers and I can't put it on there.

So, I need to be able to compile it on my Ubuntu machine so that it can run on the RedHat.  

Or maybe a completely different solution would work?  

Can anyone help?
Thanks!

---

### Post by bakegoodz on 2010-01-31
Not a trivial thing since the different system have different versions of libraries and dependencies. It is probably doable, but you will have to be familiar with the building of this software and have more than a basic knowledge of compiling software. Some programs you can static build all the libraries and it make it very portable. I'm not familiar with this software software so I'm not sure the best strategy

---

### Post by bakegoodz on 2010-02-01
I checked out KeePass's website. You might try one of the Fedora rpms. Fedora is the community version of Red Hat, so it should have a good chance of working.
[http://www.keepassx.org/downloads](http://www.keepassx.org/downloads)

---

### Post by Kawaiii on 2010-02-01
I downloaded the rpm and tried to use it, but it still gave me an error because I don't have qt4.3 on the computer.  I need to find some way to include what it needs from qt, right?

---

### Post by jimbob on 2010-02-01
Why not convert the .rpm to .dpkg using alien?

---

### Post by Kawaiii on 2010-02-01
> **jimbob said:**
> Why not convert the .rpm to .dpkg using alien?
Will this include qt4? That really seems to be the reason I can't get it to work on the computers.

---

### Post by jimbob on 2010-02-02
I don't know but it only takes a few minutes to give it a try.

---

### Post by bakegoodz on 2010-02-06
The only reason to use alien is use a rpm on a Debian based distro

You can add qt with your package manager
I use only Debian based distros, so I not familiar with Red Hat package managers. I heard people talk about yum, I have also heard of Package kit, which I think might be a  GUI front end for yum.

---

