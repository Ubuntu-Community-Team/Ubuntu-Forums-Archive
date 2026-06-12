---
title: "webcam: advice before purchasing"
date: 2010-03-23
forum: General Help
---

### Post by jeanmarc on 2010-03-23
hello,
did you test a webcam which is immediatly recognized by ubunty 9.10 and works well on skype?
thank you in advance ++

---

### Post by darolu on 2010-03-23
Check this link out, is a list of Ubuntu supported webcams: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

Any of these should work too: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

---

### Post by jeanmarc on 2010-03-23
> **darolu said:**
> Check this link out, is a list of Ubuntu supported webcams: [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCameras)

Any of these should work too: [http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html)

thank you, darolu, for your advice. i was interested to have the direct experience of someone who has a webcam which works directly well. i have a logitech 5000 pro that i don't succeed to install. so i would prefer to avoid to buy a second webcam which would not work properly.

---

### Post by darolu on 2010-03-23
Your Logitech Pro5000 is listed here (it should work automatic): [https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech](https://wiki.ubuntu.com/HardwareSupportComponentsMultimediaWebCamerasLogitech)

It uses the **uvcvideo** driver, more info here: [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

Although Linux 2.6.26 and newer includes the Linux UVC driver natively. You will not need to download the driver manually.

Try executing this command in a terminal (applications - accessories - terminal):
```
sudo modprobe uvcvideo
```

That should load the driver, then plug your webcam and it should be installed automatically.

If it doesn't work after this, type this in your terminal (right after plugging your webcam):
```
dmesg | tail
```
This information will provide useful info to solve your problem; your Logitech Camera does work (at least it should work) with Ubuntu and you shouldn't need to buy a new camera.

Just to answer your question about "someone who has a webcam that works directly well", I have a Genius webcam, it works well automatic; it is not very good though.

By the way, what application are you using to test your webcam? it may be a configuration problem in your application.

---

### Post by jeanmarc on 2010-03-23
> **darolu said:**
> 

Try executing this command in a terminal (applications - accessories - terminal):
```
sudo modprobe uvcvideo
```That should load the driver, then plug your webcam and it should be installed automatically.


thank you for your kind help.

here is what i get with the sudo command :

```

jean-marc@precisionM90:~$ sudo modprobe uvcvideo
[sudo] password for jean-marc: 
FATAL: Error inserting uvcvideo (/lib/modules/2.6.31-20-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```

---

### Post by jeanmarc on 2010-03-23
and here what i get with the dmesg command, after having pluged the logitech 5000:

```

jean-marc@precisionM90:~$ dmesg | tail
[ 8520.218389] sd 2:0:0:0: [sdb] Add. Sense: Invalid field in cdb
[ 8520.221612] sd 2:0:0:0: [sdb] Unit Not Ready
[ 8520.221617] sd 2:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 8520.221625] sd 2:0:0:0: [sdb] Add. Sense: Invalid field in cdb
[ 8520.223488] sd 2:0:0:0: [sdb] Unit Not Ready
[ 8520.223492] sd 2:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 8520.223500] sd 2:0:0:0: [sdb] Add. Sense: Invalid field in cdb
[ 8521.217285] sd 2:0:0:0: [sdb] Unit Not Ready
[ 8521.217292] sd 2:0:0:0: [sdb] Sense Key : Illegal Request [current] 
[ 8521.217302] sd 2:0:0:0: [sdb] Add. Sense: Invalid field in cdb


```

---

### Post by jeanmarc on 2010-03-23
> **darolu said:**
> 
By the way, what application are you using to test your webcam? it may be a configuration problem in your application.

i tried with cheese and camorama. both don't find the webcam.

---

### Post by jeanmarc on 2010-03-23
but the webcam is recognized with the "lsusb" command:

```

Bus 001 Device 012: ID 07ab:fc88 Freecom Technologies 
Bus 001 Device 011: ID 05af:0802 Jing-Mold Enterprise Co., Ltd 
Bus 001 Device 010: ID 059f:0323 LaCie, Ltd LaCie d2 Drive USB2
Bus 001 Device 009: ID 045e:0024 Microsoft Corp. Trackball Explorer
Bus 001 Device 008: ID 046d:08c5 Logitech, Inc. QuickCam Pro 5000
Bus 001 Device 007: ID 0b97:7762 O2 Micro, Inc. Oz776 SmartCard Reader
Bus 001 Device 005: ID 050d:0307 Belkin Components 
Bus 001 Device 004: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 001 Device 003: ID 413c:0058 Dell Computer Corp. Port Replicator
Bus 001 Device 002: ID 413c:a005 Dell Computer Corp. Internal 2.0 Hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

```

---

### Post by darolu on 2010-03-23
Seems like the cause of your problem is the uvcvideo module as it seems to be corrupted:
```
jean-marc@precisionM90:~$ sudo modprobe uvcvideo
[sudo] password for jean-marc: 
FATAL: Error inserting uvcvideo (/lib/modules/2.6.31-20-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)
```
To see what the exact problem is, call "dmesg | tail" right after you do "sudo modprobe uvcvideo", it is possible that the module (uvcvideo.ko) error prints more than 10 strings so using "dmesg" (without tail) may be necessary.

It's most likely that you'll be needing to reinstall the 'uvcvideo' module, I don't know if there is a "easy way" to install it (i.e. apt-get) but this link explains how to install it using the source code: [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

---

### Post by jeanmarc on 2010-03-24
> **darolu said:**
> To see what the exact problem is, call "dmesg | tail" right after you do "sudo modprobe uvcvideo", it is possible that the module (uvcvideo.ko) error prints more than 10 strings so using "dmesg" (without tail) may be necessary.


thank you for your kind help.

here is what i get when typing "dmesg" after having typed "sudo..." :

```

jean-marc@precisionM90:~$ sudo modprobe uvc video
[sudo] password for jean-marc: 
FATAL: Module uvc not found.

jean-marc@precisionM90:~$ dmesg | tail
[   30.269307] ppdev: user-space parallel port driver
[   31.575696] EXT4-fs (sda7): barriers enabled
[   31.588376] kjournald2 starting: pid 1677, dev sda7:8, commit interval 5 seconds
[   31.588753] EXT4-fs (sda7): internal journal on sda7:8
[   31.588757] EXT4-fs (sda7): delayed allocation enabled
[   31.588760] EXT4-fs: file extents enabled
[   31.588905] EXT4-fs: mballoc enabled
[   31.588920] EXT4-fs (sda7): mounted filesystem with ordered data mode
[   43.386973] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[  504.501069] CE: hpet increasing min_delta_ns to 15000 nsec

```

---

### Post by jeanmarc on 2010-03-24
> **darolu said:**
> 

It's most likely that you'll be needing to reinstall the 'uvcvideo' module, I don't know if there is a "easy way" to install it (i.e. apt-get) but this link explains how to install it using the source code: [https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

i tried to start the installation of the uvcvideo module, but it seems that there is no linux-headers package (sorry but it is in french):
"impossible to find the "linux-headers-unmae -r" package."

```

jean-marc@precisionM90:~$ uname -r
2.6.31-20-generic
jean-marc@precisionM90:~$ sudo apt-get install linux-headers-'uname -r'
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
E: Impossible de trouver le paquet linux-headers-uname -r
jean-marc@precisionM90:~$ 

```

---

### Post by darolu on 2010-03-24
Oh well the documentation is not very clear, you are supposed to change "uname -r" with your result. "uname -r" prints your kernel version.
This is what I get (c'est en espagnol, je suis désolé):
```
dan@midoslin:~$ uname -r
**2.6.31-20-generic**
dan@midoslin:~$ sudo apt-get install linux-headers-**2.6.31-20-generic**
[sudo] password for dan: 
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
linux-headers-**2.6.31-20-generic** ya está en su versión más reciente.
fijado linux-headers-**2.6.31-20-generic** como instalado manualmente.
0 actualizados, 0 se instalarán, 0 para eliminar y 3 no actualizados.
dan@midoslin:~$
```
My headers were already installed so you can't see the whole process but that's the idea.

If you don't feel comfortable using the terminal, you can install them with Synaptic at *System - Administration - Synaptic package manager*, search for "linux-headers" and install the one that matches the kernel you are using (the one you find with 'uname -r').

Now that you are going to compile and install the source code, you will need these other packages; they containt gcc and make; both used in that tutorial:
```
$ sudo apt-get install build-essential automake cmake
```
By the way, this is a extremely useful trick: press TAB to auto-complete commands, for example, when typing your linux-headers, type "**lin**" press TAB and it will auto-complete "linux" keep typing and pressing TAB "linux-headers-2.6.3" TAB, etc... that way the rist of a typo is minimal.

Bonne chance!

---

### Post by jeanmarc on 2010-03-24
hello darolu,

thanks again for your kind advices and attention.

i succeeded to install the linux headers and the automake cmake.

now i am stopped during the installation of the uvc support as described here:
[https://help.ubuntu.com/community/UVC](https://help.ubuntu.com/community/UVC)

i don't find the uvcvideo... directory :

"Navigate to the 'uvcvideo-1b4c7a6b9d26' directory (or some similar name) containing the source. If you want to customize which drivers to compile, run: make menuconfig"

you will find here what i find when searching uvcvideo directories :
[http://mantel1.fr/uvcdirectories.png](http://mantel1.fr/uvcdirectories.png)

so the command "make menuconfig" does not work, probably because of the wrong directory :

```

jean-marc@precisionM90:/$ make menuconfig
make: *** Pas de règle pour fabriquer la cible « menuconfig ». Arrêt.

```

---

### Post by darolu on 2010-03-24
Before you run the make command you need to be at the sources directory; navigate with "cd" command, i.e.
```
jean-marc@precisionM90:~$ **cd** gspca/linux/drivers
jean-marc@precisionM90:~/gspca/linux/drivers$ make menuconfig
```

---

### Post by jeanmarc on 2010-03-24
> **darolu said:**
> Before you run the make command you need to be at the sources directory; navigate with "cd" command, i.e.
```
jean-marc@precisionM90:~$ **cd** gspca/linux/drivers
jean-marc@precisionM90:~/gspca/linux/drivers$ make menuconfig
```

here is what i get :

```

jean-marc@precisionM90:~/gspca/linux/drivers/media/video/uvc$ make menuconfig
make: *** Pas de règle pour fabriquer la cible « menuconfig ». Arrêt.

```

*(in english : No rule for building the "menuconfig" target. Stop.)*

---

### Post by darolu on 2010-03-24
Read the INSTALL/README file so you can learn the options for 'menuconfig'; but customizing it is not necessary you can skip this step and do:
```
$ make
```

---

### Post by jeanmarc on 2010-03-26
hello darolu,
i can access the make menuconfig in the gspca folder
[I](but not in the 
/gspca/linux/drivers/media/video/uvc folder)[/I].  

but i don't succeed to set up the last line "sudo modprobe uvcvideo". 
here is what i get :
```
jean-marc@precisionM90:~/gspca$ sudo modprobe uvcvideo
FATAL: Error inserting uvcvideo (/lib/modules/2.6.31-20-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```??

in the dmesg, i get a lot of lines that i don't know how to interpret...

---

### Post by darolu on 2010-03-26
After you configured with "make menuconfig", did you run:
```
$ make
$ sudo make install
$ sudo depmod -a
```
If you did, and still get that error; it could mean your old module is still loaded, unplug your camera and remove it with:
```
$ sudo modprobe -r uvcvideo
```
After that load the module back with:
```
$ sudo modprobe uvcvideo
```
And that should be it.

---

### Post by jeanmarc on 2010-03-27
> **darolu said:**
> After you configured with "make menuconfig", did you run:
```
$ make
$ sudo make install
$ sudo depmod -a
```

these above lines work without any error.

> **darolu said:**
> 
If you did, and still get that error; it could mean your old module is still loaded, unplug your camera and remove it with:
```
$ sudo modprobe -r uvcvideo
```After that load the module back with:
```
$ sudo modprobe uvcvideo
```And that should be it.

 
when writing "sudo modprobe..." with the camera unpluged, i get that :

```

jean-marc@precisionM90:~/gspca$ sudo modprobe uvcvideo
FATAL: Error inserting uvcvideo (/lib/modules/2.6.31-20-generic/kernel/drivers/media/video/uvc/uvcvideo.ko): Unknown symbol in module, or unknown parameter (see dmesg)

```the same after having done : sudo modprobe -r uvcvideo

here is the result of the dmesg command  :
```

jean-marc@precisionM90:~/gspca$ dmesg | tail
[  714.013927] uvcvideo: disagrees about version of symbol video_devdata
[  714.013933] uvcvideo: Unknown symbol video_devdata
[  714.015179] uvcvideo: disagrees about version of symbol video_unregister_device
[  714.015183] uvcvideo: Unknown symbol video_unregister_device
[  714.015538] uvcvideo: disagrees about version of symbol video_device_alloc
[  714.015542] uvcvideo: Unknown symbol video_device_alloc
[  714.015863] uvcvideo: disagrees about version of symbol video_register_device
[  714.015867] uvcvideo: Unknown symbol video_register_device
[  714.016754] uvcvideo: disagrees about version of symbol video_device_release
[  714.016758] uvcvideo: Unknown symbol video_device_release

```with gstreamer-properties, the webcam is not recognized at all.

???

---

