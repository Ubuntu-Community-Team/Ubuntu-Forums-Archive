---
title: "Installing Mono 2.8 on Ubuntu via shell script"
date: 2010-11-06
forum: General Help
---

### Post by Quadunit404 on 2010-11-06
I have a shell script on my computer that will download and install Mono 2.8 on Ubuntu. I'm just wondering if it's safe to use.

Why do I want to do this? To use C# and ASP.NET 4.0.

Here's the contents of the script:

```
#!/bin/bash

TOPDIR=$(pwd)
BUILDDIR=$TOPDIR/build
DLDDIR=$TOPDIR/downloads

export PATH=/usr/local/bin:$PATH


echo "updating existing system"
sudo apt-get update
sudo apt-get upgrade -y

echo "installing prerequisites"
sudo apt-get install -y build-essential libc6-dev g++ gcc libglib2.0-dev pkg-config subversion apache2 apache2-threaded-dev bison gettext autoconf automake libtool libpango1.0-dev libatk1.0-dev libgtk2.0-dev libtiff4-dev libgif-dev libglade2-dev

mkdir -p $BUILDDIR

echo
echo "downloading mono packages"
echo

cd $BUILDDIR

wget http://ftp.novell.com/pub/mono/sources/xsp/xsp-2.8.tar.bz2
wget http://ftp.novell.com/pub/mono/sources/mod_mono/mod_mono-2.8.tar.bz2
wget http://ftp.novell.com/pub/mono/sources/mono/mono-2.8.tar.bz2
wget http://ftp.novell.com/pub/mono/sources/libgdiplus/libgdiplus-2.8.tar.bz2
wget http://ftp.novell.com/pub/mono/sources/gtk-sharp212/gtk-sharp-2.12.10.tar.bz2

cd $BUILDDIR
bunzip2 -df xsp-2.8.tar.bz2
tar -xvf xsp-2.8.tar

bunzip2 -df mod_mono-2.8.tar.bz2
tar -xvf mod_mono-2.8.tar

bunzip2 -df mono-2.8.tar.bz2
tar -xvf mono-2.8.tar

bunzip2 -df libgdiplus-2.8.tar.bz2
tar -xvf libgdiplus-2.8.tar

bunzip2 -df gtk-sharp-2.12.10.tar.bz2
tar -xvf gtk-sharp-2.12.10.tar

echo
echo "building and installing mono packages"
echo


cd $BUILDDIR
cd libgdiplus-2.8
./configure --prefix=/usr/local
make
sudo make install

cd $BUILDDIR
cd mono-2.8
./configure --prefix=/usr/local
make
sudo make install

cd $BUILDDIR
cd gtk-sharp-2.12.10
./configure --prefix=/usr/local
make
sudo make install

cd $BUILDDIR
cd xsp-2.8
./configure --prefix=/usr/local
make
sudo make install

cd $BUILDDIR
cd mod_mono-2.8
./configure --prefix=/usr/local
make
sudo make install
cd $BUILDDIR

echo
echo "done"
```

My current Mono installation is setup like this (according to whereis:) /usr/bin/mono /etc/mono /usr/lib/mono /usr/lib64/mono /usr/share/mono

---

### Post by directhex on 2010-11-06
Just keep in mind that you will have two GACs - e.g. GTK# apps won't run for you anymore if they try to use /usr/local/bin/mono but that mono install has no GTK# in its GAC

---

### Post by Quadunit404 on 2010-11-06
So, what you're saying is in order to continue using Banshee (the only Mono app I currently have installed other than MonoDevelop and an incredibly basic WebKit browser I made in MonoDevelop that lacks a GUI and over 90% of the functionality a browser has due to it only having 12 lines of code total) I'll need to use the Mono installed in /usr/bin/mono as my default Mono runtime, right?

---

### Post by directhex on 2010-11-07
> **Quadunit404 said:**
> So, what you're saying is in order to continue using Banshee (the only Mono app I currently have installed other than MonoDevelop and an incredibly basic WebKit browser I made in MonoDevelop that lacks a GUI and over 90% of the functionality a browser has due to it only having 12 lines of code total) I'll need to use the Mono installed in /usr/bin/mono as my default Mono runtime, right?

Both Banshee and MonoDevelop will use the mono executable in $PATH.

Your best bet (something I've never bothered with since I don't support unpackaged Mono) is to duplicate /usr/share/cli-common/runtimes.d/mono as something like mono28, with fixed paths to make it relevant to your /usr/local install - then run dpkg-reconfigure mono-gac. That should install all libraries from the system GAC into your self-built GAC, now and automatically in the future.

---

