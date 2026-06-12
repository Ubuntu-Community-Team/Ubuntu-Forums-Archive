---
title: "Cisco VPN INstallation Problem"
date: 2009-10-17
forum: General Help
---

### Post by LWhitson2 on 2009-10-17
Alright, I am still new to this whole Linux thing and am trying to work out a problem.  I am required to install this Cisco VPN program on my computer in order to access my university resources.  Unfortunately, they do not offer any type of tech support for Linux users so I am kind of stuck.  After I download the package they tell me to run the vpn_install script and I get the following errors:

Making module
make -C /lib/modules/2.6.28-15-generic/build SUBDIRS=/home/lunitsond/Downloads/vpnclient modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.28-15-generic'
scripts/Makefile.build:46: *** CFLAGS was changed in "/home/lunitsond/Downloads/vpnclient/Makefile". Fix it to use EXTRA_CFLAGS.  Stop.
make[1]: *** [_module_/home/lunitsond/Downloads/vpnclient] Error 2
make[1]: Leaving directory `/usr/src/linux-headers-2.6.28-15-generic'
make: *** [default] Error 2
Failed to make module "cisco_ipsec.ko".

Can anyone help me out here?

Thanks,
Bryce

---

### Post by skatinjj on 2009-10-17
Run the script from a terminal and put:

```
sudo
```

i.e:  sudo script.bin

at the beginning. This will let you run the script as root and may fix your problem.

---

### Post by Marti68 on 2009-10-19
Looks a lot like what I need.  Can I check; is the script the standard Cisco install or a script written by / for your Uni'

Is there a definitive Cisco client version to aim for?  My company are using 4.6 on the XP laptops.

Thanks for your patience with us newbies.

---

### Post by maflynn on 2009-10-20
Check out the steps I found here on this site
[http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/comment-page-2/#comment-253682](http://www.longren.org/2007/05/17/how-to-cisco-vpn-client-on-ubuntu-704-feisty-fawn/comment-page-2/#comment-253682)

Don't worry about that its referring feist-fawn, it worked well for me on 9.04.  I am having an issue with with the cisco vpn on the beta of 9.10 though

---

