---
title: "ROOT CERN update"
date: 2010-06-18
forum: General Help
---

### Post by tjb891 on 2010-06-18
Ok so I used the ROOT software made by the CERN group for work. The ubuntu official repositories only have version 5.18 when I need to use version 5.26 (about 5 versions later). Does anyone know another repository that might have it? Possibly a Debian repository?

---

### Post by gzarkadas on 2010-06-18
Debian sid (unstable) has 5.24 as a source package; see [http://packages.debian.org/sid/root-system](http://packages.debian.org/sid/root-system). You will have to make a source install. Go to [http://root.cern.ch/drupal/content/production-version-526](http://root.cern.ch/drupal/content/production-version-526) to get the 5.26 version; the page has also a link to instructions of how to build from source.

---

### Post by tjb891 on 2010-06-20
Ok, so can I add the debian files somehow to a repository so synaptic can handle the install?

---

### Post by gzarkadas on 2010-06-20
You will not gain anything from entering debian repositories in you sources list; the package you want is a source package and you will have to compile it to create the binaries. In addition it is a large package with many dependencies and mixing repositories from different distributions is a good way to mesh up your system. I suggest to either:

    * Follow the instructions in [this blog]("http://jayblanco.wordpress.com/2010/02/08/compiling-root-from-source-in-ubuntu-9-10/") to build and install the 5.26 version in the classic way (./configure make make-install). You'll get the latest version, but the installation won't be recorded by the standard package management scheme.

    * Follow the instructions below to build and install the 5.24 version as a binary .deb package. Slightly older version, but gives the benefit of integration with the standard package management scheme.

Steps:

1. Make a directory (say ~/src/root-system) to place the source files.

2. Download the files shown by the three links in the `Download root-system' section of page [http://packages.debian.org/source/sid/root-system](http://packages.debian.org/source/sid/root-system) into the source directory created in step 1.

3. Open a Nautilus window and navigate to this directory.

4. Right-click on each compressed archive and select `Extract Here' from the context menu that appears. You should end up with a sub-directory `root-system-5.24.00.orig' and a file`root-system_5.24.00-1.diff'.

4. Now open a terminal window (menu `Applications|Accessories|Terminal) and type the following commands:
```

cd ~/src/root-system
patch -p0 < root-system_5.24.00-1.diff

```This patches the upstream sources with the ubuntu-specific patches for the package .

5. Ensure you have installed the proper build tools in your system.
```

sudo apt-get build-essential fakeroot

```6. Query the source package to fulfill dependencies.
```

cd ./root-system-5.24.00.orig
sudo apt-get build-dep root-system

```This will install all of the package dependencies.
Your package is now ready for compilation.

7. Use the debian package tools to build binary packages (.deb files):

I a copying here the instructions contained in [http://www.debian.org/doc/FAQ/ch-pkg_basics.html](http://www.debian.org/doc/FAQ/ch-pkg_basics.html). 

You are already, if followed instructions, inside the top directory of the build tree.

8. Create a dedicated version of your own build (so that you won't get confused later when Ubuntu releases a new version).
```

dch -l local 'some text'

```9. Now build the packages:
```

debuild -us -uc

```10. And if all go well, install them:
```

sudo dpkg -i ../*.deb

```Keep a backup of the locally created .deb files to be able to de-install / install the packages without recompilation.

---

### Post by tjb891 on 2010-06-21
thank you

---

### Post by dvd_it on 2010-08-27
if you want i regularly build root for ubuntu.
here you can find my packages for 64bits:
[http://sourceforge.net/projects/cernrootdebs/](http://sourceforge.net/projects/cernrootdebs/)

ciao
d

---

### Post by chenel on 2010-10-13
Do you also compile a 32-bit version? ...

---

### Post by dvd_it on 2011-01-13
> **chenel said:**
> Do you also compile a 32-bit version? ...
unfortunately no, I don't... :(
d

---

### Post by dvd_it on 2011-05-20
Since many people asked me to build alsa the 32bits version here you are Root 5.28.00c packed for ubuntu and debian [http://sourceforge.net/projects/cernrootdebs/files/32bits!/](http://sourceforge.net/projects/cernrootdebs/files/32bits!/)

hope this helps
d

---

