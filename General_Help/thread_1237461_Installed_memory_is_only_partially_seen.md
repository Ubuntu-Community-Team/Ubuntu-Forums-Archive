---
title: "Installed memory is only partially seen"
date: 2009-08-11
forum: General Help
---

### Post by apesa on 2009-08-11
I am running Jaunty 9.04 on a Lenovo T61 and have had no problems, runs great. I just swapped 2X2GB sodimms in place of the 1X1GB sodimm I initially had for memory. I am running a LAMP server and the 1GB was not enough. everything seems ok except for the "System Monitor" showing only 3GB. in Terminal, sudo lshw reports 2X2gb modules and I also ran "System Test" and it reported the same. The BIOS reports 4096MB as well.

I want to make sure I have 4GB available, so should I beleive the 3GB I see in System Monitor? Or should I assume it is using all 4GB? Since I oringinally installed Jaunty on 1GB, is there something I should tweak in order to maximize available memory?

Thanks for all replies in advance.

Pat

---

### Post by EvilMarshmallow on 2009-08-11
It's a physical limitation on address space.  You're not getting the full benefit of 4 GB RAM.

[http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/](http://samiux.wordpress.com/2008/01/10/how-to-use-4-gb-ram-on-a-32-bit-ubuntu/)

---

### Post by apesa on 2009-08-11
Thanks for the help. It is fixed. I scoured the help and support files for that last night as well as googled it and did not find this link... Thanks again

---

