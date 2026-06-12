---
title: "Installing Juniper Network Connect Software?"
date: 2012-02-12
forum: General Help
---

### Post by boy18nj on 2012-02-12
Most of the posts on google say how to access VPN using juniper network connect. They assume every company would provide jar files required to setup juniper network connect.
They say you go to your VPN site, it would by default install in your home directory you should now have “.juniper_networks”.

At least not in my case, basically i am looking how to install juniper network connect on my ubuntu 11.10 machine. Rest things later how to connect. First i want to know how to get all necessary stuff to install “.juniper_networks” on my machine and from which site should i download?

Thanks

---

### Post by boy18nj on 2012-02-13
Any help here?

---

### Post by boy18nj on 2012-02-15
Any help here? Did anyone have this issue?

---

### Post by kperrier on 2012-03-08
We are working on making this work as my job. Unfortunately unless the VPN software on the appliance is set up to support it, you will not be able to install network connect, as it will be pushed out to you when you log in. It is not a separate package for you to install.

This might help if your SA/IC are setup for your client: [http://blog.daftdba.com/2012/02/how-to-set-up-juniper-network-connect.html](http://blog.daftdba.com/2012/02/how-to-set-up-juniper-network-connect.html)

---

### Post by Mark Phelps on 2012-03-09
Can confirm that the Jupiter client SW is pushed out to you after you attempt to establish a VPN connection.  Don't know of any way to request it separately.

---

