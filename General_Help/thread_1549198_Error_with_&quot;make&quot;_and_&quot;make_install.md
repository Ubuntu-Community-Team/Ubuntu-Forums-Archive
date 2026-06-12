---
title: "Error with &quot;make&quot; and &quot;make install&quot;  &quot; *.ko failed to build!&quot;"
date: 2010-08-09
forum: General Help
---

### Post by JazzTrmpter on 2010-08-09
I have been trying to install a new driver for my wireless USB adapter, and I've been getting some "make" command problems and error messages.  Specifically, I am installing the RaLink rt2570 USB Enhanced Driver to work with my Linksys WUSB100 adapter (chipset RaLink Rt2870).
I downloaded the package and used the readme from inside the package here:
[http://homepages.tu-darmstadt.de/~p_larbig/wlan/]("http://homepages.tu-darmstadt.de/%7Ep_larbig/wlan/")

Here's what I have done directly after download to my desktop:

```
david@ubuntu:~$ cd /home/david/Desktop/rt2570-k2wrlz-1.6.4/Module
david@ubuntu:~/Desktop/rt2570-k2wrlz-1.6.4/Module$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
rt2570.ko failed to build!
make: *** [module] Error 1
david@ubuntu:~/Desktop/rt2570-k2wrlz-1.6.4/Module$ sudo make install
make[1]: Entering directory `/home/david/Desktop/rt2570-k2wrlz-1.6.4/Module'
make[2]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[2]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
rt2570.ko failed to build!
make[1]: *** [module] Error 1
make[1]: Leaving directory `/home/david/Desktop/rt2570-k2wrlz-1.6.4/Module'
make: *** [modules_install] Error 2
david@ubuntu:~/Desktop/rt2570-k2wrlz-1.6.4/Module$ 


```I don't see what the problem is.  Any ideas?

---

### Post by JazzTrmpter on 2010-08-09
I did some more research and I believe it is because the current version of the driver is not compatible with my kernel 2.6.32.   So, I believe I just have to wait until a new release comes out.

Would it be wise to downgrade kernels to the latest supported version for the driver?  The last supported version is 2.6.29.

---

### Post by FSHero on 2010-09-19
Hi JazzTrmpter,

I've actually been trying to install the discontinued SerialMonkey drivers, found at:
[http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt2570-legacy-final-cvs/rt2570-cvs-daily.tar.gz/download](http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt2570-legacy-final-cvs/rt2570-cvs-daily.tar.gz/download)
(title page: [http://sourceforge.net/projects/rt2400/files/](http://sourceforge.net/projects/rt2400/files/))

The last release of the rt2570 driver was apparently on 2009-05-12. I got it working with Kubuntu Hardy (8.04) i386. I've recently done a fresh install of Lucid on the same system. As usual, I've installed build-essential and linux-headers-`uname -a`. However, I get the following error messgaes:

```

$ make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
rt2570.ko failed to build!
make: *** [module] Error 1
$

```

Could it be that the Lucid kernels (I'm running 2.6.32-24-generic) are so new that the driver cannot compile on these systems? I've run out of ideas.

OTOH, I didn't realise that someone was still developing drivers for rt2570 chipset. (Newest files in his 1.6.4 source code archive are dated 2009-05-19.) I think this ASPj fellow might just provide us with the solution!

Until then... just gotta sit tight I guess.

---

### Post by FSHero on 2010-09-19
For the record, I just tried compiling the ASPj 1.6.4 drivers. They failed, again, with the same error as JazzTrmpter.

```

$ sudo make
make[1]: Entering directory `/usr/src/linux-headers-2.6.32-24-generic'
  Building modules, stage 2.
  MODPOST 0 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.32-24-generic'
rt2570.ko failed to build!
make: *** [module] Error 1

```

---

### Post by Escoba on 2010-12-09
It's a pitty that ubuntu staff couldn't help with this, I'm also trying to install this and I can't get it running, did someone got the solution?

Thanks on regards.

---

### Post by Escoba on 2011-01-26
Sorry for bumping, but I found a solution yesterday for linksys WUSB series drivers, that is installing the .inf driver (downloading it from [www.cisco.com](www.cisco.com)) using ndiswrapper. Worked out for me, but I couldn't use nm-applet, so I installed wicd and problem solved ;)

---

### Post by JazzTrmpter on 2011-01-27
I believe the kernels are too new to work with Lucid. And unfortunately, the drivers are not being developed anymore. I asked the driver writer by email and he said development has stopped. I just saved myself any more hastle and picked up a pci wireless card made by hawking technologies. Works great and easy to compile the modified driver from serial monkey (to be used with aircrack-ng suite). 

Unfortunately, I believe there is no "real" solution to the problem. You'll most likely have to use Ndiswrapper and another driver. Thanks Escoba for your contribution.

---

### Post by joelstitch on 2011-05-25
> **Escoba said:**
> Sorry for bumping, but I found a solution yesterday for linksys WUSB series drivers, that is installing the .inf driver (downloading it from [www.cisco.com]("http://www.cisco.com")) using ndiswrapper. Worked out for me, but I couldn't use nm-applet, so I installed wicd and problem solved ;)


Can you please provide instructions on how to do this? I was able to install it with **sudo ndiswrapper -i netr70.inf**, but when I try to find wireless signals nothing happens. I turn off my computers wireless card first, and I use wicd.

---

