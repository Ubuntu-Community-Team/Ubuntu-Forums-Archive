---
title: "gnuradio build"
date: 2011-02-02
forum: General Help
---

### Post by cjejuni on 2011-02-02
hi all:
am installing/building gnuradio and following the instructions from the gnuradio.org/wiki. seemed like i got everything it needs: pre-req pkgs, git UHD and gnuradio pkgs. built UHD without problems. am at the gnuradio configuring/building, bootstrapped fine. but when i ran ./configure, errored with:

les@Liquid:/gnuradio$ ./configure
bash: ./configure: No such file or directory

there is no configure file in directory. any help on this.

tia,
cj

---

### Post by lykeion on 2011-02-02
If you don't specifically need the latest git version, you can install prepackaged binary from Ubuntu repositories:
sudo apt-get install gnuradio

If you do still want to compile it yourself, look at the compile instructions for Ubuntu: [http://gnuradio.org/redmine/wiki/gnuradio/UbuntuInstall](http://gnuradio.org/redmine/wiki/gnuradio/UbuntuInstall)
It has some notes which may be important:
# If you want to use GNU Radio with UHD you have to switch to the "next" branch before you bootstrap, see UHD instructions
# If you are building from a release .tar.gz rather than git you should skip the bootstrap step.

---

### Post by cjejuni on 2011-02-02
it was the idea to build from scratch, learn how the process go! newbie programmer here. like first post, it was building smoothly until the missing ./configure in gnuradio. UHD (from git) is built already, it went all fine. thanks for the insight...
cj

---

### Post by lykeion on 2011-02-02
Tested to download sources from git, and ran ./bootstrap, then ./configure. Worked fine (although errors because I didn't install the pre-requisited packages). Step-by step:
1. Install pre-requisits (assuming Ubuntu Lucid or later)
```
sudo apt-get install libfontconfig1-dev libxrender-dev libpulse-dev swig g++ automake autoconf libtool python-dev libfftw3-dev libcppunit-dev libboost-all-dev libusb-dev fort77 sdcc sdcc-libraries libsdl1.2-dev python-wxgtk2.8 git-core guile-1.8-dev libqt4-dev python-numpy ccache python-opengl libgsl0-dev python-cheetah python-lxml doxygen qt4-dev-tools libqwt5-qt4-dev libqwtplot3d-qt4-dev pyqt4-dev-tools
```
2. Make dir and download sources from git (will take a while)
```
cd; mkdir gnuradio-git; cd gnuradio-git
git clone http://gnuradio.org/git/gnuradio.git
```
3. Enter dir and bootstrap
```
cd gnuradio
./bootstrap
```
4. Configure (I always change prefix to /usr)
```
./configure --prefix=/usr
```
5. Compile and install (I have a quad core CPU, if you don't just skip the -j parameter, the make check is optional)
```
make -j4
make check 
sudo make install
```

---

### Post by cjejuni on 2011-02-02
thanks again. that's what i am following to build. the problem i am running into is:
the "./configure" file is missing from the gnuradio directory where compilation is taking place. 
thanks,
cj

---

### Post by cjejuni on 2011-02-06
downloaded the git from the gnuradio.org, followed the instructions from there, it worked.
thanks.

---

