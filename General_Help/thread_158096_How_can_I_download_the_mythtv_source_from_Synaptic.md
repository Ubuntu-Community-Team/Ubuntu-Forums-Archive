---
title: "How can I download the mythtv source from Synaptic?"
date: 2006-04-10
forum: General Help
---

### Post by RoboJ1M on 2006-04-10
Hi,

currently I have the following line (only) in my sources.list

```
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
```

Which I thought would allow me to add the mythtv source package
[URL="http://packages.ubuntu.com/breezy/source/mythtv"]
http://packages.ubuntu.com/breezy/source/mythtv[/URL]

But I only seem to have a list of packages I already have installed.

Can anybody help?

Thanks,

J1M.

---

### Post by frikazoyd on 2006-04-10
Just checking, you tried ```
sudo apt-get source mythtv
``` right?

---

### Post by RoboJ1M on 2006-04-10
Aha.

That'll do it.

I also required the binary package list for the dependancies

Actually it's the build dependencies I'm interestd in so I can build 0.19

Can I only ge sources with apt-get then?

Is that not implemented in Synaptic?

Thanks,

J1M.

---

### Post by RoboJ1M on 2006-04-10
OK, with my sources set as:

```
deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
```

I now get:
```

james@HAL:~$ sudo apt-get -V build-dep mythtv
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for mythtv could not be satisfied.

```

Not very helpfull is it? :s

J1M.

---

### Post by RoboJ1M on 2006-04-10
Fixed it:
```

deb http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ breezy-security main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu/ breezy-updates main restricted universe multiverse

```
 And now I get:
```

The following NEW packages will be installed:
  g++-3.4 libartsc0-dev libasound2-dev libaudio-dev libdvb-dev libexpat1-dev
  libfontconfig1-dev libfreetype6-dev libgl1-mesa-dev libglib2.0-dev
  libglu1-mesa-dev libice-dev libjpeg62-dev liblame-dev liblcms1-dev
  liblircclient-dev libmng-dev libmysqlclient14-dev libogg-dev libpng12-dev
  libqt3-headers libqt3-mt-dev libsm-dev libstdc++6-dev libvorbis-dev
  libx11-dev libxau-dev libxcursor-dev libxext-dev libxft-dev libxi-dev
  libxinerama-dev libxmu-dev libxmu-headers libxrandr-dev libxrender-dev
  libxt-dev libxv-dev libxvmc-dev libxvmc1 libxxf86vm-dev qt3-dev-tools x-dev
  x11proto-core-dev x11proto-gl-dev x11proto-input-dev x11proto-kb-dev
  x11proto-randr-dev x11proto-render-dev x11proto-video-dev x11proto-xext-dev
  x11proto-xf86vidmode-dev x11proto-xinerama-dev xlibs-static-dev
0 upgraded, 54 newly installed, 0 to remove and 2 not upgraded.
Need to get 18.0MB of archives.

```

Now, that Plus

[COLOR="Red"]56k MODEM!![/COLOR]

[COLOR="Red"]= PAIN[/COLOR]

Ah well...

J1M.

---

