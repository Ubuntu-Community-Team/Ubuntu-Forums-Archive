---
title: "configuring boost and gnuradio"
date: 2010-02-23
forum: General Help
---

### Post by deviouskoopa on 2010-02-23
Hey all, I'm trying to install boost and eventually gnuradio according to these instructions:
[http://gnuradio.org/redmine/wiki/gnuradio/UbuntuInstall](http://gnuradio.org/redmine/wiki/gnuradio/UbuntuInstall)

however, where it says to configure with:
```
$ ./configure --prefix=$BOOST_PREFIX --with-libraries=thread,date_time,program_options

```
this fails, because there is no "configure" file in the boost_1_42_0 folder, I think. So I tried 
```
sudo apt-get install libboost-dev
```
which looks like it installed boost1.38.0, but after doing this I realized I don't know how to do this step accordingly:
```
git clone http://gnuradio.org/git/gnuradio.git

cd gnuradio
export LD_LIBRARY_PATH=$BOOST_PREFIX/lib     # As per the instructions for installing Boost

./bootstrap
./configure --with-boost=$BOOST_PREFIX   # As per the instructions for installing Boost
make

```

Does anyone here have experience with boost and/or gnuradio that can help me out? Running Xubuntu 9.10 on eeePC-900. Thanks a lot!

---

