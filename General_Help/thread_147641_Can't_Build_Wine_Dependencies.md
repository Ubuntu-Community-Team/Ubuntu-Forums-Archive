---
title: "Can't Build Wine Dependencies"
date: 2006-03-20
forum: General Help
---

### Post by aqualad on 2006-03-20
I'm attempting to install wine so that I can run World of Warcraft, but something went wrong in my wine installation or something.

I have wine installed currently, I downloaded wine-0.9.6.tar.bz2 and extracted it into /home/aqualad/wine-0.9.6 and then patched it with two patches: 

wine-cvs-glx.diff 
wine-wow-fixes.patch

using the command:

```
patch -p1 < wine-cvs-glx.diff
patch -p1 < wine-wow-fixes.patch
```

Then I went into /home/aqualad/wine-0.9.6 and ran
```
./configure
make depend && make
sudo make install
```

I ended up having to download a few packages to get it to install properly, but it seemed to be working.  I ran the command
```
wine
```
so that it would build the fake c drive, but whenever i try to run programs I get this:

```
aqualad@aqualad:/etc$ wine /home/aqualad/Desktop/n_v14.exe
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
err:imagelist:ImageList_ReplaceIcon no color!
Application tries to create a window, but no driver could be loaded.
Make sure that your X server is running and that $DISPLAY is set correctly.

```

I noticed that other people had gotten that error too, so to solve it they ran 

```
sudo apt-get build-dep wine
```

to fix it, but when I run that I get this:

```
aqualad@aqualad:/etc$ sudo apt-get build-dep wine
Password:
Reading package lists... Done
Building dependency tree... Done
E: Build-dependencies for wine could not be satisfied.
```

So yeah,  how do I get 'sudo apt-get build-dep wine' working properly?  I thought that maybe it was cause of my repositories, so here's sources.list:

```
#deb cdrom:[Ubuntu 5.10 _dapper Badger_ - Release i386 (20051012)]/ dapper main restricted

## Uncomment the following two lines to fetch updated software from the network
deb-src http://archive.ubuntu.com/ubuntu dapper main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src http://archive.ubuntu.com/ubuntu dapper universe

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe

deb http://archive.ubuntu.com/ubuntu dapper multiverse universe main restricted
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper main restricted


##addon

## Uncomment the following two lines to fetch updated software from the network
deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
##deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
##deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted


deb http://wine.sourceforge.net/apt/ binary/
deb-src http://wine.sourceforge.net/apt/ source/

```

---

