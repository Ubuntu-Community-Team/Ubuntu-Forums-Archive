---
title: "&quot;Uninstall&quot; custom kernel"
date: 2010-02-19
forum: General Help
---

### Post by markus_orreilly on 2010-02-19
I was recently trying to get VMWare Server 1.0 working on Ubuntu 9.10 (kernel 2.6.31-19) by following the directions here: [http://www.howtoforge.com/how-to-install-vmware-server-1.0.x-on-an-ubuntu-9.10-desktop](http://www.howtoforge.com/how-to-install-vmware-server-1.0.x-on-an-ubuntu-9.10-desktop)  The directions didn't work for me, and now I run into errors now and then when installing new packages.  I'm trying to revert back to the original generic kernel, but with no luck.  I'm decent with common functions in linux, but this is beyond my experience.  Any tips?

---

### Post by amsterdamharu on 2010-02-19
When you boot do you get a grub menu? If so just boot off another kernel and remove the custom kernel from your /boot directory. Usually when ubuntu does a kernel update it leaves the old one in there so you can boot into the old one.

You can use synaptic to uninstall the newest kernel and re-install it (I assume you've altered the newest kernel)

---

