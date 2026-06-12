---
title: "Grab Package Version using grep"
date: 2010-07-19
forum: General Help
---

### Post by ncwilde43 on 2010-07-19
Can someone tell me how to grab the install package version of virtualbox-ose using dpkg and grep?

All I have so far is:
```
dpkg -s virtualbox-ose | grep '[0-9]\.[0-9]\.[0-9]'
```

I want 3.2.0 from the [FONT="Courier New"]dpkg -s virtualbox-ose [/FONT]
```

username@computer:~$ dpkg -s virtualbox-ose
Package: virtualbox-ose
Status: install ok installed
Priority: optional
Section: misc
Installed-Size: 31316
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: i386
Version: [COLOR="Red"]3.2.0[/COLOR]-dfsg-1ubuntu1~lucid1
Depends: libc6 (>= 2.11), libcurl3 (>= 7.16.2-1), libgcc1 (>= 1:4.1.1), libpng12-0 (>= 1.2.13-4), libpython2.6 (>= 2.6), libsdl1.2debian (>= 1.2.10-1), libssl0.9.8 (>= 0.9.8k-1), libstdc++6 (>= 4.2.1), libvncserver0, libx11-6 (>= 0), libxcursor1 (>> 1.1.2), libxext6 (>= 0), libxml2 (>= 2.7.4), libxmu6, libxt6, zlib1g (>= 1:1.1.4), python (>= 2.4), python-central (>= 0.6.11), adduser
Recommends: virtualbox-ose-dkms (= 3.2.0-dfsg-1ubuntu1~lucid1), virtualbox-ose-qt (= 3.2.0-dfsg-1ubuntu1~lucid1), libgl1-mesa-glx | libgl1, libqt4-opengl (>= 4:4.5.3), libqtcore4 (>= 4:4.5.3), libqtgui4 (>= 4:4.5.3)
Suggests: virtualbox-guest-additions, libasound2, libpulse0, vde2
Conflicts: virtualbox, virtualbox-2.0, virtualbox-2.1, virtualbox-2.2, virtualbox-3.0
Conffiles:
 /etc/default/virtualbox-ose 467417a44a8cc0a80482f55c27e93c80
 /etc/init.d/virtualbox-ose 7db3ea1ccf905c4d8b6e03b363cf7f49
Description: x86 virtualization solution - base binaries
 VirtualBox is a free x86 virtualization solution allowing a wide range
 of x86 operating systems such as Windows, DOS, BSD or Linux to run on a
 Linux system.
 .
 This package provides the binaries for the Open Source Edition of
 VirtualBox. The virtualbox-ose-dkms package is also required in order
 to compile the kernel modules needed for virtualbox-ose. A graphical user
 interface for VirtualBox is provided by the package virtualbox-ose-qt.
Homepage: http://www.virtualbox.org/
Original-Maintainer: Debian Virtualbox Team <pkg-virtualbox-devel@lists.alioth.debian.org>
Python-Version: >= 2.4

```

---

### Post by iponeverything on 2010-07-19
There are tons of ways to do it, this just one..

```
dpkg -s virtualbox-ose |grep ^Version|awk -F\- '{print $1}'
```

---

### Post by bodhi.zazen on 2010-07-19
> **iponeverything said:**
> There are tons of ways to do it, this just one..

```
dpkg -s virtualbox-ose |grep ^Version|awk -F\- '{print $1}'
```
  Nice one.

If you want only the numbers, add another awk

```
dpkg -s virtualbox-ose |grep '^Version'|awk -F\- '{print $1}'|awk '{print $2}'
```

Also I had to quote the grep expression

---

### Post by ncwilde43 on 2010-07-19
> **bodhi.zazen said:**
> Nice one.

If you want only the numbers, add another awk

```
dpkg -s virtualbox-ose |grep '^Version'|awk -F\- '{print $1}'|awk '{print $2}'
```

Also I had to quote the grep expression

Exactly what I was looking for.  Thanks for the fast responses.

---

