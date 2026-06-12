---
title: "MagicQ on 10.04"
date: 2010-05-16
forum: General Help
---

### Post by OccasionallyY on 2010-05-16
My uncle recently decided to install Linux. He does lighting for various bands and such, and he decided to continue using MagicQ on Linux. However, I was never able to get it off the ground for him. I downloaded the source code so that I could build MagicQ, but I kept running into to the 'cannot find libftdi.so.1' error that is discussed in the installation manual. It's entirely likely that I am just being dumb, but I am stuck. Does anyone know the proper fix for this issue?

---

### Post by soundpartner on 2010-08-25
> **OccasionallyY said:**
> My uncle recently decided to install Linux. He does lighting for various bands and such, and he decided to continue using MagicQ on Linux. However, I was never able to get it off the ground for him. I downloaded the source code so that I could build MagicQ, but I kept running into to the 'cannot find libftdi.so.1' error that is discussed in the installation manual. It's entirely likely that I am just being dumb, but I am stuck. Does anyone know the proper fix for this issue?
i am running magicq without problems in 32 bit ubuntu 10.04

you need to install the libftdi1 driver in ubuntu
sudo aptitude install libftdi1
and then it works... 

magicq is a 32 bit program so in 64 bit it takes a bit of magic.
we have to install a 32 bit libftdi driver in ubuntu 64 bit

mkdir sptemp && cd sptemp/
wget [http://archive.ubuntu.com/ubuntu/pool/main/libf/libftdi/libftdi1_0.17-1_i386.deb](http://archive.ubuntu.com/ubuntu/pool/main/libf/libftdi/libftdi1_0.17-1_i386.deb)
dpkg -x libftdi1_0.17-1_i386.deb .
gksudo "cp usr/lib/libftdi.so.1* /usr/lib32/"
cd .. && rm -r sptemp

---

