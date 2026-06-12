---
title: "apt-get install question"
date: 2010-06-02
forum: General Help
---

### Post by pwaugh on 2010-06-02
I have installed Mercurial:

~$ sudo apt-get install Mercurial

but, of course, this is not the latest version.  It is version 1.4.3.

If I want to install the latest stable version, 1.5.4 from source, do I need to uninstall 1.4.3 first to avoid confusing apt-get???

patrick

---

### Post by Isaacgallegos on 2010-06-02
I've never used mercurial, but I would recommend removing the old one. however, your only other option is to compile the source (tar.gz file) since their website recommends debian/ubuntu users to use
sudo apt-get install mercurial 
which you already tried.

---

### Post by pwaugh on 2010-06-02
Yeah, the whole point is I will compile from source, which is not a problem, I've done it before.  I just need to know definatively IF I MUST apt-get remove in order to not confuse apt-get.

Not looking for a recommendation, looking for a definative answer.  I know it would be a safe assumption to just do it, but I want to know if it MUST be done.

---

### Post by jpkotta on 2010-06-08
Apt will not be confused unless you somehow make the new mercurial known to it.  A simple "make install" won't do that.  However, it will be needlessly difficult to avoid uninstalling the package first.  At the very least, you need to make sure that the new version doesn't overwrite the ubuntu package (it shouldn't, because it installs to /usr/local by default), and that everything uses the mercurial installation you want it to.  

You may want to check out the Mercurial PPAs: [https://launchpad.net/~mercurial-ppa](https://launchpad.net/~mercurial-ppa)

---

### Post by pwaugh on 2010-06-08
> **jpkotta said:**
> Apt will not be confused unless you somehow make the new mercurial known to it.  A simple "make install" won't do that.  However, it will be needlessly difficult to avoid uninstalling the package first.  At the very least, you need to make sure that the new version doesn't overwrite the ubuntu package (it shouldn't, because it installs to /usr/local by default), and that everything uses the mercurial installation you want it to.  

You may want to check out the Mercurial PPAs: [https://launchpad.net/~mercurial-ppa](https://launchpad.net/~mercurial-ppa)

Thanks for the info.  It will indeed mess up an apt-get uninstall as they are both installed to /usr/local/...   but basically I went ahead an uninstalled it first as I suspected it would be a problem even if apt-get wouldn't "know" about the other version, and there was no need to have both present.

I'll check out the link you gave, thanks.

patrick

---

