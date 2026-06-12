---
title: "adding a PPA"
date: 2010-04-14
forum: General Help
---

### Post by oleink on 2010-04-14
If i add a ppa in the terminal and udate and install it, If i am to type "sudo apt-get update" later in the terminal when a new release comes out will it update my program??

---

### Post by mcduck on 2010-04-14
> **oleink said:**
> If i add a ppa in the terminal and udate and install it, If i am to type "sudo apt-get update" later in the terminal when a new release comes out will it update my program??

Yes. That's the very idea why to use repositories and package management instead of just downloading the package manually.

Although "apt-get update" doesn't update your programs, it updates the information about available packages & their versions. "apt-get upgrade" is the command that actually downloads & installs updates for your programs. (Usually you'd run both commands at the same time, first "update" to check if there are any updates available and the "upgrade" to install those updates.)

---

### Post by oleink on 2010-04-14
Thats what i figured but it always appears that they change their update area so I lose the updates anyway.  Like aka songbird, the only one I've found has an old versiion that doesn't support video...

---

### Post by oleink on 2010-04-14
Why is this??

---

### Post by loell on 2010-04-14
you're not loosing any, if you still want specific version of a program instead of the latest in the PPA. 

you can,

```
sudo apt-get install PackageName=SpecificVersion
```

---

### Post by oleink on 2010-04-14
I want the newer version of songbird but the ppa is for an old version

---

### Post by oleink on 2010-04-15
does anyone know where the new version is?

---

### Post by steveneddy on 2010-04-15
> **oleink said:**
> does anyone know where the new version is?

developer ppa is at

[https://launchpad.net/~songbird-daily/+archive/ppa](https://launchpad.net/~songbird-daily/+archive/ppa)

and the regular download page is at

[http://www.getsongbird.com/system-requirements.php](http://www.getsongbird.com/system-requirements.php)

The development ppa will give you the "bleeding edge" version of songbird.

Good luck

---

