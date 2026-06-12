---
title: "wireless dongle issue"
date: 2009-09-04
forum: General Help
---

### Post by rastro123 on 2009-09-04
Hi folks,
I have a linksys wusb54gc v.3 usb dongle that I'v been trying to get working on my hp dv5 laptop with an inbuilt wireless broadcom 4312 without sucess. I dont wish to use the inbuilt wireless as it wont do monitor mode etc. I'v been trying various versions of rt73 drivers from ralink but I'm getting nowhere. Does anyone have any experience of this dongle and can advice me please? Here are the results of my latest attempt to install the driver:
boo@my-laptop:~$ cd src
boo@my-laptop:~/src$ rt73-k2wrlz-3.0.3
bash: rt73-k2wrlz-3.0.3: orden no encontrada
boo@my-laptop:~/src$ cd rt73-k2wrlz-3.0.3
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3$ sudo make
[sudo] password for boo: 
make: *** No se especificó ningún objetivo y no se encontró ningún makefile.  Alto.
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3$ /Module
bash: /Module: No existe el fichero ó directorio
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3$ cd Module
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3/Module$ sudo make
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-15-generic'
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rtmp_main.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/mlme.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/connect.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rtusb_bulk.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rtusb_io.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/sync.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/assoc.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/auth.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/auth_rsp.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rtusb_data.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rtmp_init.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/sanity.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rtmp_wep.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rtmp_info.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rtmp_tkip.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/wpa.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/md5.o
  CC [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rt2x00debug.o
  LD [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rt73.o
  Building modules, stage 2.
  MODPOST 1 modules
  CC      /home/boo/src/rt73-k2wrlz-3.0.3/Module/rt73.mod.o
  LD [M]  /home/boo/src/rt73-k2wrlz-3.0.3/Module/rt73.ko
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-15-generic'
*** Module rt73.ko built successfully
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3/Module$ sudo make install
*** Install module in /lib/modules/2.6.28-15-generic/extra ...
make[1]: se ingresa al directorio `/usr/src/linux-headers-2.6.28-15-generic'
  INSTALL /home/boo/src/rt73-k2wrlz-3.0.3/Module/rt73.ko
  DEPMOD  2.6.28-15-generic
make[1]: se sale del directorio `/usr/src/linux-headers-2.6.28-15-generic'
/sbin/depmod -a
*** Update /etc/modprobe.d/ralink alias for wlan*
*** Install firmware in /lib/firmware ...
*** Check old config ...
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3/Module$ modprobe rt73
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
FATAL: Error inserting rt73 (/lib/modules/2.6.28-15-generic/extra/rt73.ko): Operation not permitted
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3/Module$ modprobe
Usage: modprobe [-v] [-V] [-C config-file] [-d <dirname> ] [-n] [-i] [-q] [-b] [-o <modname>] [ --dump-modversions ] <modname> [parameters...]
modprobe -r [-n] [-i] [-v] <modulename> ...
modprobe -l -t <dirname> [ -a <modulename> ...]
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3/Module$ modprobe rt73
WARNING: All config files need .conf: /etc/modprobe.d/ralink, it will be ignored in a future release.
FATAL: Error inserting rt73 (/lib/modules/2.6.28-15-generic/extra/rt73.ko): Operation not permitted
boo@my-laptop:~/src/rt73-k2wrlz-3.0.3/Module$ 
As you can see, it starts to go ok, then I get the ''fatal error''. Another one I installed after being told that that's the driver I need installed ok, but again, the pc did not see it. Most grateful for any help.

---

### Post by Bachstelze on 2009-09-04
Firstly, the language of this forum is English, so you'll have better luck if your error messages are displayed in English. Secondly, you shouldn't neet to install the rt73 driver. Adapters based on the rt73 are supported out of the box.

---

### Post by rastro123 on 2009-09-04
Im a brit but I live in spain and my s.o. is in spanish. It doesn't seem to be supported out of the box. I spoke to linksys and they say it's not supported with linux. Many people on other forums have said to me that I need the rt73 driver, but I'm getting nowhere fast with it. What exactly do you mean that it's supported out of the box pls?. The light on the dongle does not come on, although I see it when I do lsusb. Also, if I was to get it to work, do I have to disable the inbuilt device, or will this happen automatically? Thanks.

---

### Post by rastro123 on 2009-09-05
why bother sending me a message? I've asked you what you mean about ''out of the box'' - it doesnt work. The guys at the linux forum suggested better help here, but you dont answer me mr hymn to life. Nice one mate.

---

### Post by rastro123 on 2009-09-06
is there no-one that knows how to make a dongle work for wireless? I find it hard to believe. Why does this guy say it works from the box? Does he mean I plug it in and it works?- It doesn't. It shows up in lsusb, but thats about it. C'mon folks- any help pls?

---

### Post by rogerp1 on 2009-09-06
I got an edimax dongle working that uses the rt73 driver.

I downloaded it from here [http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt73-legacy-final-cvs/rt73-cvs-daily.tar.gz/download]("http://sourceforge.net/projects/rt2400/files/Final%20software%20release/rt73-legacy-final-cvs/rt73-cvs-daily.tar.gz/download"). It eventually worked after i installed WICD instead of network manager

---

### Post by rastro123 on 2009-09-07
thanks roger, I'll try it mate.

---

### Post by cab.abraham on 2009-10-25
Amigo "out of the box" se refiere que no necesitas nada para poder usarlo solamente lo pones y se supone que funcione. Osea cuando vas a cagar tu celular tu lo enchuflas y ya y el celular se carga. Lo mismo pasa con el usb wifi adaptor. Pero me parece que no esta funcionando con las vercion 9.04 yo tenia antes Ubuntu 8.04 y me funcionaba pero parece que le sacaron el supporte de ese equipo en las verciones nuevas de Ubuntu...

---

