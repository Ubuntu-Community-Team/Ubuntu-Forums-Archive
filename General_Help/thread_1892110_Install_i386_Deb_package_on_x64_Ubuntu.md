---
title: "Install i386 Deb package on x64 Ubuntu"
date: 2011-12-07
forum: General Help
---

### Post by gmsalomao2 on 2011-12-07
I'm trying to install the package "cutecw_1.0-0ubuntu11101_i386.deb" from this website: [http://www.hamtools.org/](http://www.hamtools.org/)

The problem is that the architecture is i386 while my Ubuntu is x86_64.
I've tried dpkg -i --force-architecture, but something goes wrong.

Here's the output:
```
# dpkg -i --force-architecture cutecw_1.0-0ubuntu11101_i386.deb
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 39806 package 'b2gmailnotifier.1e5171da61ae26f47cb00a9ab285cc8775905a13.1':
 error in Version string 'v0.24publicalpha': version number does not start with digit
Selecting previously deselected package cutecw:i386.
(Reading database ... 326546 files and directories currently installed.)
Unpacking cutecw:i386 (from cutecw_1.0-0ubuntu11101_i386.deb) ...
dpkg: dependency problems prevent configuration of cutecw:i386:
 cutecw:i386 depends on libqtmultimediakit1 (>= 1.1.0).
dpkg: error processing cutecw:i386 (--install):
 dependency problems - leaving unconfigured
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Errors were encountered while processing:
 cutecw:i386

```I see the dependency problem, but I get the same output (except for the dependency problem) after installing libqtmultimediakit1 ](*,)

---

### Post by kurt18947 on 2011-12-07
I don't know what the difference is - if any- but I use
```
dpkg  -i  --force-all {package name}
```when installing Brother 32 bit printer drivers on 64 bit systems per Brother's instructions.

---

### Post by gmsalomao2 on 2011-12-07
> **kurt18947 said:**
> I don't know what the difference is - if any- but I use
```
dpkg  -i  --force-all {package name}
```when installing Brother 32 bit printer drivers on 64 bit systems per Brother's instructions.


After installing the libqtmultimediakit1:

```
# dpkg -i --force-all Desktop/cutecw_1.0-0ubuntu11101_i386.deb
dpkg: warning: parsing file '/var/lib/dpkg/available' near line 39833 package 'b2gmailnotifier.1e5171da61ae26f47cb00a9ab285cc8775905a13.1':
 error in Version string 'v0.24publicalpha': version number does not start with digit
Selecting previously deselected package cutecw:i386.
(Reading database ... 326559 files and directories currently installed.)
Unpacking cutecw:i386 (from .../cutecw_1.0-0ubuntu11101_i386.deb) ...
dpkg: cutecw:i386: dependency problems, but configuring anyway as you requested:
 cutecw:i386 depends on libqtmultimediakit1 (>= 1.1.0).
Setting up cutecw:i386 (1.0-0ubuntu1) ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...

```Then:
```

# cutecw
cutecw: error while loading shared libraries: libQtMultimediaKit.so.1: wrong ELF class: ELFCLASS64

```

---

### Post by BC59 on 2011-12-07
You have to install first the package ia32-libs:

```
sudo apt-get install ia32-libs
```

and then to install any 32bit package you run it like this:

```
sudo dpkg -i - -force-architecture thepackage.deb
```

---

### Post by lykwydchykyn on 2011-12-07
If this is 11.10 with multiarch enabled (it is by default), I think you need to install the i386 version of libqtmultimediakit.  I'm still figuring out how this multi-arch thing works, it's not like previous versions.

Give that a try, though.

---

### Post by gmsalomao2 on 2011-12-07
> **BC59 said:**
> You have to install first the package ia32-libs:

```
sudo apt-get install ia32-libs
```and then to install any 32bit package you run it like this:

```
sudo dpkg -i - -force-architecture thepackage.deb
```

It's already installed.
I think the problem is with this specific package.

---

### Post by gmsalomao2 on 2011-12-07
> **lykwydchykyn said:**
> If this is 11.10 with multiarch enabled (it is by default), I think you need to install the i386 version of libqtmultimediakit.  I'm still figuring out how this multi-arch thing works, it's not like previous versions.

Give that a try, though.


Yes, this is 11.10.

How do I find the i386 package of libqtmultimediakit? I tried apt-cache search, but it not even returned the x64 version.

EDIT: I could find libqtmultimediakit1 on Synaptic. But not the i386 version.

---

### Post by lykwydchykyn on 2011-12-07
> **gmsalomao2 said:**
> It's already installed.
I think the problem is with this specific package.

If you open synaptic and search for "libqtmultimediakit" you should see two package:

 - **libqtmultimediakit1**, which I'm guessing is installed
 - **libqtmultimediakit1:i386**, which is probably not.  Try installing this one.

---

### Post by lykwydchykyn on 2011-12-07
> **gmsalomao2 said:**
> Yes, this is 11.10.

How do I find the i386 package of libqtmultimediakit? I tried apt-cache search, but it not even returned the x64 version.

EDIT: I could find libqtmultimediakit1 on Synaptic. But not the i386 version.

If you browse synaptic, do you see any :i386 packages?

---

### Post by gmsalomao2 on 2011-12-07
> **lykwydchykyn said:**
> If you browse synaptic, do you see any :i386 packages?

Now I see it.. somehow.

But it depends on two other packages, and those two other packages depends on lots of other packages and require lots of changes on existing packages.... They all are probably gonna change to i368.. is that safe?

---

### Post by lykwydchykyn on 2011-12-07
> **gmsalomao2 said:**
> Now I see it.. somehow.

But it depends on two other packages, and those two other packages depends on lots of other packages and require lots of changes on existing packages.... They all are probably gonna change to i368.. is that safe?

I can't say for sure, though if it's not conflicting or removing anything I can't see that it'd be a problem.  Without actually seeing details of what it's going to do, I don't know.

---

### Post by gmsalomao2 on 2011-12-07
Ok.. that's fine. I can still run that on Maemo (Nokia N900) :)
I'll try to find another morse code training app.
Thanks guys.

---

