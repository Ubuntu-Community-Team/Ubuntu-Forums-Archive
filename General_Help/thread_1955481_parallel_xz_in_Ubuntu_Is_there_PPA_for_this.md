---
title: "parallel xz in Ubuntu? Is there PPA for this?"
date: 2012-04-09
forum: General Help
---

### Post by Kdar on 2012-04-09
I want to install parallel xz. When I checked in Ubuntu's repository, it wasn't there. Is there any PPA for this?

---

### Post by r-senior on 2012-04-09
Which version? It appears to be in 12.04:

```
$ apt-cache search --names-only xz
[COLOR="Red"]xz-lzma - XZ-format compression utilities - compatibility commands
xz-utils - XZ-format compression utilities
[/COLOR]python-txzookeeper - Twisted-based Asynchronous Libraries for Apache Zookeeper.
xzdec - XZ-format compression utilities - tiny decompressors
xzgv - Picture viewer for X with a thumbnail-based selector
xzip - Interpreter of Infocom-format story-files
xzoom - magnify part of X display, with real-time updates

```

---

### Post by Kdar on 2012-04-09
I have xz-utils installed, this is for regular, serial version.

But I know there are two parallel implementations of xz around, one is pxz and another is pixz.

From GitHub:
pixz
[https://github.com/vasi/pixz](https://github.com/vasi/pixz)
pxz
[http://jnovy.fedorapeople.org/pxz/](http://jnovy.fedorapeople.org/pxz/)
And also, I know Arch Linux's AUR has builds for them:
[https://aur.archlinux.org/packages.php?ID=36362](https://aur.archlinux.org/packages.php?ID=36362)
[https://aur.archlinux.org/packages.php?ID=49137](https://aur.archlinux.org/packages.php?ID=49137)

However, I am using Ubuntu at my school, where I am trying to run some tests and I am wondering if anyone know if there is a deb file for those or if there is a ppa.

---

### Post by r-senior on 2012-04-10
You could always compile it. Do you have build-essential installed?

I got the archive from github and these were the steps to compile it:

```
sudo apt-get install liblzma-dev libarchive-dev
tar xzvf vasi-pixz-bd56f57.tar.gz
cd vasi-pixz-bd56f57
make

```

You should end up with a pixz executable in the source directory. Move that to ~/bin, add that to your path and you are set.

---

### Post by Kdar on 2012-04-10
Ah thanks. I will give it a try.

---

