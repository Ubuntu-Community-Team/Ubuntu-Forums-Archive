---
title: "LEGO Mindstorms RCX2.0 on ubuntu"
date: 2011-05-18
forum: General Help
---

### Post by Affrikka on 2011-05-18
Hey everyone,

A few friends and I wanted to try our hand at robotics, and instead of spending $400 on the intellibrain, we decided to take my old LEGO Mindstorms Robotics Invention System and program it in a 'real' language, not the brick programming thing that comes with it. 
Of the three of us, I was assigned to be the programmer (although we will probably all help each other out on everyone's task) mainly because I enjoy programming the most, building the least, and I own the thing so if I break it it's my fault, not theirs. I do have my system dual-booted with windows 7, but windows 7 is really retarded and won't install the driver for the USB IR Tower properly (they stopped supporting it, I guess that old mac commercial with the "printer doesn't work? Buy a new one!" is true... sigh..) and I would much rather have it running on ubuntu anyway.

I've looked at several different things, brickOS, leJOS, and this NQC with Bricx but I can't seem to find a really comprehensible guide on getting things set up.

Does anyone have any of these things running, and can you share how you got it set up please?

Thanks you!


Mathieu


p.s. I didn't really know where to put this topic, so if there's a better place please move it. Thanks.

---

### Post by Affrikka on 2011-05-18
bump

---

### Post by Affrikka on 2011-05-21
bump again, does anyone know?

---

### Post by silhusk on 2011-08-21
Hi, I come a bit late... but I hope it can be useful anyway.

Here is how I installed brickOS on Ubuntu 11.04 (Natty).

There is no package in Ubuntu anymore, so take the one from Debian sid:
  [http://packages.debian.org/unstable/devel/brickos](http://packages.debian.org/unstable/devel/brickos)
The package contains libraries and header files for brickOS, and two utilities ('dll' and 'firmdl3') that send programs and firmware to the RCX.
In `/usr/share/doc/brickos/examples` there are some examples. Install the `brickos-doc` package for the documentation, if you want.

Also the compiler must be downloaded from Debian
  [http://packages.debian.org/sid/gcc-h8300-hms](http://packages.debian.org/sid/gcc-h8300-hms)

Now install the two downloaded packages and one from Ubuntu repositories
```
  sudo dpkg -i brickos_0.9.0.dfsg-6_amd64.deb
  sudo apt-get install binutils-h8300-hms
  sudo dpkg -i gcc-h8300-hms_3.4.6-6_amd64.deb
```


Try to compile the demos in a local folder as follows
```
  cp -R /usr/share/doc/brickos/examples/demo .
  cd demo/
  gunzip trailerbot.c.gz
  make
```

Now let's load the firmware to the RCX. Connect the IR Tower and power on the RCX.
(I'm using the USB tower here, if you have a serial one take a look at `man firmdl3`)
  ```
sudo firmdl3 --tty=/dev/usb/legousbtower0 /usr/lib/brickos/brickOS.srec
```

And finally load the 'sound' demo
  ```
sudo dll --tty=/dev/usb/legousbtower0 sound.lx
```

Unfortunately, you always have to use sudo due to the access permissions for /dev/usb/legousbtower0.

---

