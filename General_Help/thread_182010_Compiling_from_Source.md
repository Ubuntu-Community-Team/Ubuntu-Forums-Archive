---
title: "Compiling from Source"
date: 2006-05-25
forum: General Help
---

### Post by vinodis on 2006-05-25
Too bad that build-essential are not installed by default.

How to get the build-essential package AT_ONCE with all their dependencies [without]("http://packages.ubuntu.com/") using apt-get?. I have no internet connection on my Linux PC at home.
and 
How can I edit the PATH variable on a global scale?

TIA

---

### Post by Sef on 2006-05-25
Do you have access to the internet and a burner elsewhere?

If you do go to packages.ubuntu.com > Dapper (or Breezy) > Development > Click on build-essential to see the other packages you need to download and burn.

---

### Post by vinodis on 2006-05-25
if you see my message's hyperlink - i have listed that website already. I have access to internet connection here at office. I can download here. But the problem is that build-essential has dependency with say 10 other packages and they in turn have dependencies with another 10 each.. How do I get em all?

TIA

---

### Post by Sef on 2006-05-25
Here is the list:

> build-essential
 |Depends: libc6-dev
  Depends: <libc-dev>
    libc6-dev
  Depends: gcc
  Depends: g++
  Depends: make
  Depends: dpkg-dev



---

### Post by vinodis on 2006-05-25
But see.. the gcc in turn has dependencies with :-

cpp (>= 4:4.0.1-3)
g++-4.0 (>= 4.0.1-2)
gcc (>= 4:4.0.1-3)
gcc-4.0 (>= 4.0.1-2)

I am totally lost!

---

### Post by Ragazzo on 2006-05-25
When I install build-essential with Synaptic, it says "Please insert the disk labeled:
Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)
in drive /cdrom/". 
So I guess it's on the installation CD?

---

### Post by az on 2006-05-25
[QUOTE=Ragazzo]When I install build-essential with Synaptic, it says "Please insert the disk labeled:
Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)
in drive /cdrom/". 
So I guess it's on the installation CD?[/QUOTE]
It is on the cd.

The only problem is that the applications are all built with gcc-4.0 and that is present on the cd.  However, ther kernel was build with gcc-3.4, which is *not* on the cd (an oversight).  To build a kernel module, you need to fetch the three gcc-3.4 packages yourself.

---

### Post by vinodis on 2006-05-26
Today I downloaded the dapper ISO. Planning to Upgrade. Hope all these problems go away.

---

