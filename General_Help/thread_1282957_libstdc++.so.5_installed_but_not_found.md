---
title: "libstdc++.so.5 installed but not found"
date: 2009-10-05
forum: General Help
---

### Post by patmalcolm91 on 2009-10-05
After upgrading from jaunty to karmic beta, libstdc++5 was removed and is no longer in the repos. This library is needed for my printer driver (lexmark z515: followed [these instructions]("http://ubuntuforums.org/showthread.php?t=49714")). The printer worked fine in jaunty.

The problem in the install process is when I go to verify it's working with the z600 script, which returns:

```
./z600: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory

```

I've found the jaunty .deb package for libstdc++5 and installed it manually, but I still get the same message.

I know it's installed because ls -l /usr/lib | grep -i libstdc++ shows:
```

lrwxrwxrwx  1 root root       18 2009-10-04 22:12 libstdc++.so.5 -> libstdc++.so.5.0.7
-rw-r--rwx  1 root root   855856 2009-10-04 23:15 libstdc++.so.5.0.7
lrwxrwxrwx  1 root root       19 2009-10-04 17:19 libstdc++.so.6 -> libstdc++.so.6.0.13
-rw-r--r--  1 root root  1027760 2009-10-03 17:33 libstdc++.so.6.0.13

```

But, ldd z600 (z600 is the script to test whether the printer is installed correctly) shows:
```

	linux-gate.so.1 =>  (0xf7f40000)
	liblexprinter.so.0 => /usr/lib/liblexprinter.so.0 (0xf7f0a000)
	libstdc++.so.5 => not found
	libm.so.6 => /lib32/libm.so.6 (0xf7ee1000)
	libgcc_s.so.1 => /usr/lib32/libgcc_s.so.1 (0xf7eb5000)
	libc.so.6 => /lib32/libc.so.6 (0xf7d5d000)
	/lib/ld-linux.so.2 (0xf7f41000)

```

By the way, if it makes a difference, i'm on the 64-bit architecture and the driver packages are x86. this didn't make a difference in jaunty, but i don't know if it will in karmic.

Thanks in advance for any help.

Patrick

---

### Post by patmalcolm91 on 2009-10-05
I figured it out.

Since the driver is for 32-bit, it was looking for a 32-bit libstdc++.so.5, so I went to packages.ubuntu.com/jaunty and downloaded and extracted the libstdc++5 deb file and manually placed the so files in /usr/lib32/

Now everything works great.

---

### Post by rrfx on 2009-10-11
Same issue here with IBM Lotus Domino Server. 

Downloaded this package: [http://packages.ubuntu.com/jaunty/i386/libstdc++5/download]("http://packages.ubuntu.com/jaunty/i386/libstdc++5/download") 

and dropped the files into /usr/lib32 worked a treat! 

Thanks.

---

### Post by ayourk on 2009-11-02
I've tracked this problem out down to a change in ia32-libs.  The package ia32-libs_2.7ubuntu6.1_amd64.deb has the 32-bit libstdc++.so.5 and the newer package ia32-libs_2.7ubuntu17_amd64.deb does NOT have it.  Sounds like it is time to file a bug report... ;)

EDIT: Looks like someone has already filed a bug report:

[Bug #431091]("https://bugs.launchpad.net/ubuntu/+source/ia32-libs/+bug/431091")

---

### Post by Copernicus1234 on 2009-11-07
I just installed this package and its very quick and just works without messing with anything else. Its for 32 bit machines.

[http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download)

For me, this was used to get the Google Web Toolkit local browser to work on Karmic.

---

### Post by dunnerz on 2009-11-07
> **rrfx said:**
> Same issue here with IBM Lotus Domino Server. 

Downloaded this package: [http://packages.ubuntu.com/jaunty/i386/libstdc++5/download]("http://packages.ubuntu.com/jaunty/i386/libstdc++5/download") 

and dropped the files into /usr/lib32 worked a treat! 

Thanks.

Brilliant thanks, this worked perfectly for me for getting checkpoint snx (ssl network extender) working for me. 

Thanks.

---

### Post by rrfx on 2009-11-07
Copernicus1234 I wouldn't be comfortable installing 32-bit libs on an amd64 install, and also where possible choose the Ubuntu ones rather than debian's versions - see the better link to Ubuntu's package above.

Note that deb packages can be extracted by by typing this command in a shell:
```
dpkg-deb --extract <deb> <directory>
```

---

### Post by KiLaHuRtZ on 2009-11-10
This may help, [http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000]("http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000").  It's a little tutorial I posted on my website.;)

---

### Post by rrfx on 2009-11-11
> **KiLaHuRtZ said:**
> This may help, [http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000]("http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000").  It's a little tutorial I posted on my website.;)

Thats great, however i would recommend people dont get into the habit of installing 32-bit packages on 64-bit systems with "dpkg --force-architecture". You'll clobber something one day.

Given your instructions say to move the *installed* libs anyway, extract the files manually with "dpkg-deb --extract <deb> <temp directory>" and move them from there.

---

### Post by ayourk on 2009-11-16
Here is something that was just posted into the bug listed above:


Erik  wrote 1 hour ago: 	#17
> 
The nicest solution I found is adding this PPA: [https://launchpad.net/~jason-scheunemann/+archive/ppa](https://launchpad.net/~jason-scheunemann/+archive/ppa) to your sources with these lines:
deb [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu](http://ppa.launchpad.net/jason-scheunemann/ppa/ubuntu) karmic main

Accepting the key, and installing "lib32stdc++5" package. This is for amd64 systems.

AYourk wrote 40 minutes ago: 	#18

> Also, the following should serve as a quick way to add his ppa key to your local keyring:

```
wget -q 'http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x932062C9CD30EE56' -O - | sudo apt-key add -
```

---

### Post by sempi on 2009-11-17
> **rrfx said:**
> Copernicus1234 I wouldn't be comfortable installing 32-bit libs on an amd64 install, and also where possible choose the Ubuntu ones rather than debian's versions - see the better link to Ubuntu's package above.

Note that deb packages can be extracted by by typing this command in a shell:
```
dpkg-deb --extract <deb> <directory>
```


Also if you prefer not to copy the so into the system library folder, you can set ```
LD_LIBRARY_PATH
``` to point where the 32 bit libs are located (e.g. somewhere in your home directory.

My ubuntu eclipse start bash script:
```

#!/bin/bash

# http://code.google.com/p/google-web-toolkit/issues/detail?id=135#c30
export LIBXCB_ALLOW_SLOPPY_LOCK=true

# 32 bit libraries used for GWT
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$HOME/bin/lib32

# fix bug with mouse clicks not being registered in eclipse
export GDK_NATIVE_WINDOWS=true

export PATH=${JAVA_HOME}/bin/:$PATH
$HOME/bin/eclipse-3.5-ubuntu/eclipse $@;

```

---

### Post by hsmak_linux on 2009-12-01
Apparently, there are different ways to resolve this issue regarding the removal of libstdc++5 in Ubuntu 9.10.

I would like just to make the same contribution here. I've just posted a blog about this and it can be reached through this link:

[http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/](http://hsmak.wordpress.com/2009/12/01/how-to-fix-libstdc5-dependency-problem-in-ubuntu-9-10/)

Thx everbody!

---

### Post by afrodeity on 2010-03-09
This thread might have helped me but I tried to fix it myself and now am in trouble

[http://ubuntuforums.org/showthread.php?t=1425470](http://ubuntuforums.org/showthread.php?t=1425470)

---

### Post by hsmak_linux on 2010-03-10
> **afrodeity said:**
> This thread might have helped me but I tried to fix it myself and now am in trouble

[http://ubuntuforums.org/showthread.php?t=1425470](http://ubuntuforums.org/showthread.php?t=1425470)

You already had my reply!

Good luck!

---

### Post by amoskittelson on 2010-04-01
Thanks all!  I was getting 

**libstdc++.so.5: cannot open shared object file: No such file or directory**

when trying to install Xilinx 9.2i under Karmic. This fixed my problem pronto (after 2 hours of searching!). Thanks.

---

### Post by ab0032 on 2011-03-29
> **KiLaHuRtZ said:**
> This may help, [http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000](http://www.digitalenigma.net/directory.php?include=archives&msgid=2009111000).  It's a little tutorial I posted on my website.;)

Thank you, your instructions helped me get my Epson Aculaser CX11NF to work, it also needed the 32 bit libstdc++5.

---

