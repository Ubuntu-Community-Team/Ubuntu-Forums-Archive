---
title: "Amarok 2 was removed after update. I can't install anymore"
date: 2009-08-31
forum: General Help
---

### Post by jac0117 on 2009-08-31
I installed amarok 2 using this guide:
[http://monespaceperso.org/blog-en/2009/03/15/how-to-install-amarok-2-on-ubuntu-810/](http://monespaceperso.org/blog-en/2009/03/15/how-to-install-amarok-2-on-ubuntu-810/)

I fell in love with the new Amarok UI. I imported my music library and after Ubuntu installed some updates Amarok 2 was removed. I'm using Intrepid.

Now I'm not able to install Amarok 2 anymore. I get the following error:

amarok-kde4:

Package amarok-kde4 has no available version, but exists in the database.
This typically means that the package was mentioned in a dependency and never uploaded, has been obsoleted or is not available with the contents of sources.list

The following repository is in the third party sources:
[http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu](http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu)

Has anyone had this problem before? I don't know how to get Amarok 2 back on. I was really starting to love it.

---

### Post by jpeddicord on 2009-08-31
Why not just install [Amarok]("apt:amarok") from the repositories? It's version 2.

Edit: scratch that. You're using Intrepid, sorry.

You seem to be using the right PPA. Check [https://launchpad.net/~kubuntu-members-kde4/+archive/ppa](https://launchpad.net/~kubuntu-members-kde4/+archive/ppa) for the full package listing and double-check your sources.list.

---

### Post by jac0117 on 2009-08-31
Thanks jacobmp92, I did as you said and get the following error when I try to install:

Status: Error: Cannot install "kdebase-runtime"

---

### Post by jac0117 on 2009-08-31
OK I finally worked. I amarok 1.4 was still running after removing it. dont' know why. I closed it and I was able to install amarok 2.

Thanks.

---

