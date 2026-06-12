---
title: "kdar in Karmic?"
date: 2010-04-24
forum: General Help
---

### Post by PerfectReign on 2010-04-24
I have to restore some files from a DAR archive I made in 2007.  Back then I was on openSUSE and used KDAR.

I can see the files but have a difficult time extracting them using the command line dar tool. I was hoping to install kdar and work with that. 

I've searched and cannot find a method for installing kdar on anything more recent than gutsy gibbon.

Any ideas?

---

### Post by gzarkadas on 2010-08-27
It can be installed by downloading the related debs and doing a local install with `dpkg -i <deb-file>'. The steps to install the last kdar package made for ubuntu (tested and verified in a Karmic system) are (first open a terminal window):

1. Enter the superuser shell (this will save some typing):
```
sudo -i
```2. Make a directory to hold locally installed debs and go there; it's a good idea to keep it permanently:

```

mkdir -p /usr/local/share/local-install
cd /usr/local/share/local-install

```3. Get kdar package and needed libs from [Ubuntu pool]("http://archive.ubuntu.com/ubuntu/pool/") (these are in older releases, so for newer releases we need to get and locally install them):

```

wget -w10 [http://archive.ubuntu.com/ubuntu/pool/universe/d/dar/libdar3c2a_2.2.4-2ubuntu2_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/d/dar/libdar3c2a_2.2.4-2ubuntu2_i386.deb)
wget -w10 [http://archive.ubuntu.com/ubuntu/pool/universe/k/kdar/kdar_2.0.6-0ubuntu3_i386.deb](http://archive.ubuntu.com/ubuntu/pool/universe/k/kdar/kdar_2.0.6-0ubuntu3_i386.deb)

```4. Install the packages (order them to satisfy dependencies):

```

dpkg -i libdar3c2a_2.2.4-2ubuntu2_i386.deb
dpkg -i kdar_2.0.6-0ubuntu3_i386.deb

```5. Leave the superuser shell

```
exit
```I have run kdar and it looks functional, with one serious exception: it does not recognise my utf8 localised filenames when I try to create an archive. But even this way it can be used to create dar command lines and certainly it is better than nothing :D. Test it for yourself and decide, there may be subtle bugs around waiting to be discovered.

If you want to have a newer version, then you must use the [upstream project]("http://sourceforge.net/projects/kdar/")'s files. Unfortunately there are no .debs (except for the amd64 architecture), so one must make a source install with configure and make. 

I have managed to configured the source tree (both 2.0.8 and 2.1.0 versions), but `make' fails with errors that seem to relate with autotools installed version. I have no more time to invest to this to debug the errors and compile; you may try it yourself if you are interested. 

Below are the steps I run to reach to the `make' stage:
```

# make a directory to hold the source and get it from upstream

mkdir ~/kdar
cd ~/kdar

# get 2.0.8 sources
wget -w10 http://sourceforge.net/projects/kdar/files/kdar/2.0.8/kdar-2.0.8.tar.bz2/download
bunzip2 kdar-2.0.8.tar.bz2
tar xvf kdar-2.0.8.tar
# now the 2.0.8 source tree is in ~/kdar/kdar-2.0.8

# get 2.1.0 sources
wget -w10 http://sourceforge.net/projects/kdar/files/kdar/kdar-2.1.0/kdar-2.1.0.tar.bz2/download
bunzip2 kdar-2.1.0.tar.bz2
tar xvf kdar-2.1.0.tar
# now the source tree is in ~/kdar/kdar-2.1.0

# get ubuntu deb patch for 2.1.0
wget -w10 http://sourceforge.net/projects/kdar/files/kdar/kdar-2.1.0/kdar_2.1.0-0ubuntu1.diff.gz/download
gunzip kdar_2.1.0-0ubuntu1.diff.gz

# apply the patch
mkdir -p kdar-2.1.0.orig 
rsync -vaxHEXAD kdar-2.1.0/ kdar-2.1.0.orig/
patch -p0 -u <kdar_2.1.0-0ubuntu1.diff
# now the debian style patched tree is in ~/kdar/kdar-2.1.0 
# and the unpatched (upstream) sources in ~/kdar/kdar-2.1.0.orig

# enter the superuser shell
sudo -i

# install needed debs (as contained in upstream's ubuntu amd64 deb)

apt-get install debhelper autotools-dev cdbs kdelibs4-dev libdar-dev zlib1g-dev libbz2-dev

# install dar and libdar, if not have done already

apt-get install libdar-dev libdar64-4 dar dar-static dar-docs

# make a directory to hold locally installed debs; it's a good idea to keep it permanently

mkdir -p /usr/local/share/local-install
cd /usr/local/share/local-install

# get packages needed for configure to finish (libarts1-dev and dependencies)
# these are in interpid, so for newer distros we need to get and locally install them

wget -w10 http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0_1.5.10-0ubuntu1_i386.deb
wget -w10 http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libartsc0-dev_1.5.10-0ubuntu1_i386.deb
wget -w10 http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1c2a_1.5.10-0ubuntu1_i386.deb
wget -w10 http://archive.ubuntu.com/ubuntu/pool/main/a/arts/libarts1-dev_1.5.10-0ubuntu1_i386.deb

# install the packages (order them to satisfy dependencies)

dpkg -i libartsc0_1.5.10-0ubuntu1_i386.deb
dpkg -i libartsc0-dev_1.5.10-0ubuntu1_i386.deb
dpkg -i libarts1c2a_1.5.10-0ubuntu1_i386.deb
dpkg -i libarts1-dev_1.5.10-0ubuntu1_i386.deb

# leave the superuser shell
exit

# must set KDE_PATH for configure to find KDE libraries 

export KDE_PATH=/usr/lib/kde4:/usr/lib/kde3

# the results are same for -2.0.8 and -2.1.0.orig also
cd ~/kdar/kdar-2.1.0
autoreconf
# lots of warnings, but succeeds (?)

# compiled libdar for ubuntu comes with 64bit ints; we must add this option
./configure --enable-mode=64
# succeeds

make
# fails with errors

```

---

