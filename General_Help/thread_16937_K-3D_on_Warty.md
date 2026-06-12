---
title: "K-3D on Warty"
date: 2005-02-24
forum: General Help
---

### Post by Harderlump on 2005-02-24
The graphics application K-3D is in Hoary, but not in Warty.
However, yesterday, I installed K-3D on Warty, using the packages from Debian Sarge. I've  already had them on my Debian partition. 

I installed these packages:
[list]
[*] libjasper-1.701-1_1.701.0-2_i386.deb
[*] gpp_2.24-1_i386.deb
[*] k3d_0.4.3.0-3_i386.deb
[/list]

First, I tried to install the k3d package, but there were open dependencies to the two other packages. So, I installed them before the k3d package - and it worked.
I installed the packages using "dpkg -i"

I started the application, and it works fine :-)

---

