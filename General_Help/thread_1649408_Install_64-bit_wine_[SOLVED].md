---
title: "Install 64-bit wine [SOLVED]"
date: 2010-12-20
forum: General Help
---

### Post by quietplease on 2010-12-20
Other distros have 32-bit/64-bit wine in their package managers. 

I wrote a script to automate the compiling/installation of 64-bit wine. 

script is here:
[http://www.jesseo.com/chess/64-bit-wine-ubuntu.sh](http://www.jesseo.com/chess/64-bit-wine-ubuntu.sh)

It's been tested on Ubuntu 10.10 64-bit and Xubuntu 10.10.

---

### Post by quietplease on 2010-12-20
if anyone has a suggestion for improving the script, please let me know. i'm a novice bash scripter. 

```
#!/bin/bash --
# author: Jesse Gersenson
# file: 64-bit-wine-ubuntu.sh
# version: 0.2.3
# status: working
#
#
# what's it for? 
# ------------------
# for people who want to run 64-bit *.exe programs in Ubuntu, from 32-bit GUI's. 
# 
# the script automatically compiles a 32-bit/64-bit install of wine on Ubuntu 10.10 64-bit.
# this is a temporary fix - eventually 64 bit wine will be installable from the Ubuntu 
# package manager - as is currently (written Dec 19, 2010) the case with Sabayon 5.4 and OpenSUSE 11.3.
#
#
# how to use it?
# ------------------
# 1. first, update your system. use these two lines at the command prompt:
# sudo apt-get update
# sudo apt-get upgrade
# reboot your system.
#
# 2. save the script, http://www.jesseo.com/chess/64-bit-wine-ubuntu.sh, to your 
# user's home folder /home/USERNAME
#
# 3. open a terminal and change it's permissions by entering
# sudo chmod +x 64-bit-wine-ubuntu.sh
#
# 4. run the script with the following command
# ./64-bit-wine-ubuntu.sh
#
# let it run for about an hour. it will download about 1gb of data and will compile two version of
# wine. depending on the speed of your machine
# and internet connection, the script can take a few hours. on a 800KB connection, with an i3m
# processor, it takes about 40 minuets. 
# note: don't interupt the script. it'll take a while. this message will be on the screen for a
# long time, "Configure: Finished. Do 'make' to compile wine"
#
# i hope this doesn't break your computer - 
# but i guess it could. enjoy, Jesse. 
#
echo -n "Enter the number of cpu threads to use when compiling:"
read cores
echo "$cores threads will be used."
# make a directory in the user's root folder, in one we'll be compiling 32-bit wine, in the
# other 64-bit wine
cd 
if [ -d wine64 ]
	then echo "the folder wine64 already exists."
		echo "moving wine64 to wine64-old and creating directory wine64"
		sudo mv wine64 wine64-old
		echo "if you already have a wine64-old directory - the script probably just failed. delete wine64-old manually with sudo rm -r wine64-old - then run the script again"
		mkdir wine64
	else 
		echo "creating directory wine64"
		mkdir wine64
fi
if [ -d wine32 ]
	then echo "the folder wine32 already exists"
		echo "moving it to wine32-old and creating a fresh /wine32"
		echo "if you already have a wine32-old directory - the script probably just failed. delete wine32-old manually with sudo rm -r wine32-old - then run the script again"
		sudo mv wine32 wine32-old
		mkdir "wine32"
	else 
		echo "making directory wine32"
		mkdir wine32
fi
if [ -d .wine ]
	then echo "the folder .wine already exists. renaming folder .wine2 and uninstalling wine"
		sudo mv .wine .wine2
		sudo apt-get remove wine1.0 wine1.2 wine1.3
	else
		echo "i couldn't find an installed version of wine."
		sudo apt-get remove wine1.0 wine1.2 wine1.3
fi
# add the wine repository and update all repositories.
# update the repository. -y means don't prompt us with Y/N questions. 
sudo add-apt-repository ppa:ubuntu-wine/ppa
sudo apt-get -y update
# grab wine64 development packages
if [ -e install-wine-deps.sh ]
	then echo "install-wine-deps.sh is already on your machine?! we won't download a second copy"
	else 
		echo "running: wget http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh"
		wget http://winezeug.googlecode.com/svn/trunk/install-wine-deps.sh
fi
# change permissions of the script 
chmod 755 ./install-wine-deps.sh
#
# run the script with root privileges. you'll be prompted for your root password.  
sudo sh install-wine-deps.sh
#
# grab the 32-bit dependencies for wine1.3
# note: eventually this would need to be updated to wine1.4, wine 18.2, etc
sudo apt-get -y build-dep wine1.3
sudo apt-get -y install cabextract
#
# grab wine version 1.3.9 from sourceforge and untar it
if [ -e wine-1.3.9 ]
	then echo "the folder /wine-1.3.9 was already in your root directory. i'm deleting it and will grab a fresh copy from http://switch.dl.sourceforge.net/project/wine/Source/wine-1.3.9.tar.bz2"
	sudo rm -r wine-1.3.9
	else
		echo "getting a copy of wine-1.3.9 from http://switch.dl.sourceforge.net/project/wine/Source/wine-1.3.9.tar.bz2 and extracting it to your user's root directory"
fi
wget http://switch.dl.sourceforge.net/project/wine/Source/wine-1.3.9.tar.bz2
tar -xjvf wine-1.3.9.tar.bz2
#
# change into the wine64 directory in the user's home directory. 
# change into the wine64 directory in the user's home directory. 
cd ~/wine64
#
# configure 64-bit wine
../wine-1.3.9/configure --enable-win64
#
# make the install using 5 threads. this is a good number if you have 4 processors. 
# note: change the number to -j2 if you have a dual core machine
echo "Compiling 64-bit wine. This will take 5 min - 5 hours, depending on the speed of your machine"
make -j$cores > make.log 2>&1
#
# change to the wine32 directory and build the 32 bit version of wine. tying it together 
# with the 64-bit version we just built
cd ~/wine32
../wine-1.3.9/configure --with-wine64=../wine64
echo " "
echo "64-bit wine compiled. log file saved as ~/make.log"
echo " "
echo "Now compiling 32-bit wine. This will take 5 min - 5 hours, depending on the speed of your machine"
sudo make -j$cores > make.log 2>&1
echo "finished make of 32-bit wine. now we'll run sudo make install"
#now make wine64
cd ~/wine64
echo " "
echo "32-bit make install complete. now we'll run sudo make install on the 64-bit build"
sudo make install
echo " "
echo "done."
# the script is done. 
# here are the steps one would use to use winetricks - hacked 
# to disable their disabling winetricks on 64-bit wine systems
# install cabextract, riched30, and gdiplus
#wget http://www.jesseo.com/chess/winetricks.sh
#sudo apt-get -y install cabextract
#cd
#chmod +x winetricks.sh
#./winetricks.sh riched30
#./winetricks.sh gdiplus
```

---

### Post by hakuna_matata on 2011-01-03
First, thank you for your script. It works great!

I have only a few questions. 

After last command
> ```
sudo make install
```

only **wine64** binaries are installed in **/usr/local** subdirectories. In directory **$HOME/wine64** a link to a wrapper script called **wine** gives you the possibilty to switch between **$HOME/wine64** and **$HOME/wine32**.

Do you use wine within the directory **$HOME/wine64** ?
[LIST]
[*]If yes, do you need the last command ?
[*]If no, how do you solve the problem to switch between performing 32 bit and 64 bit windows programs?
[/LIST]

Maybe, it makes sense to create a package instead of installing:  
```
cd $HOME/wine64
sudo checkinstall --install-no
```

---

### Post by kroem on 2011-01-05
Ok... so I tried and think it's installed, but I still cant run anything :( I did however not get a meny item, but I guess that's not meant to happen.

Previously (10.04 32bit) I just installed Wine from like the software centre and it created a meny, and worked... now that I got 10.10 64bit and I try to start Wine from the meny nothing happens, at all. 

Trying to install AirVideo but it just doesn't start. I HATE this, it's so damn frustrating being a noob. 

I tried your script and now I get these errors;

~/wine32$ ./wine /home/anders/Setup243.exe 
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  90
  Current serial number in output stream:  90
fixme:actctx:parse_depend_manifests Could not find dependent assembly L"Microsoft.Windows.Common-Controls" (6.0.0.0)
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  90
  Current serial number in output stream:  90
X Error of failed request:  XF86VidModeExtensionDisabled
  Major opcode of failed request:  129 (XFree86-VidModeExtension)
  Minor opcode of failed request:  6 (XF86VidModeGetAllModeLines)
  Serial number of failed request:  90
  Current serial number in output stream:  90

and then dies...


Am I doing it right? I just ran the script, do I need to do anything afterward? 

And also... how do I completely remove what I just installed? :) If I want to do a fresh try...

Thank you for your help... and the work with the script!

---

### Post by hakuna_matata on 2011-01-05
> **kroem said:**
> 
Previously (10.04 32bit) I just installed Wine from like the software  centre and it created a meny, and worked... now that I got 10.10 64bit  and I try to start Wine from the meny nothing happens, at all. 

If you have only 32 bit **windows** software, you can use the version in the software centre, too. Also under 10.10 64bit.

If you have a 64 bit windows version of a program, you need the script.
> **kroem said:**
> ```
~/wine32$ ./wine /home/anders/Setup243.exe 
```
In my opinion 64 bit wine only works in directory** ~/wine64**
```
~/wine64$ ./wine /home/anders/Setup243.exe 
```The wrapper script **wine** switches to ** ~/wine32**, if needed. But I don't know, if the 64bit windows version of AirVideo is compatible with wine.

---

### Post by kroem on 2011-01-05
Thanks! I'll try when I get home...

The problem is - i cant even get the "normal" wine (from software centre) to work. It wont even start the configuration manager... But i can still run your version with 32bit programs, if i run it from ./wine32 ?

I probably have a bigger problem, i just wish i knew how to step back, purge everything and start over. Somehow it just wont start.

---

### Post by hakuna_matata on 2011-01-05
> **kroem said:**
> Thanks! I'll try when I get home...
But i can still run your version with 32bit programs, if i run it from ./wine32 ?

Script of **quietplease **based on [http://wiki.winehq.org/Wine64](http://wiki.winehq.org/Wine64) section[B] [I]Building a shared WoW64 setup.
[/I][/B]
So the description should also work for you:
> Now you should run wine in the wine64 directory to have the Wow64 Features. The 32-bit side of such a Wow64 build is in theory supposed to work identically to a stand-alone 32-bit build.
Maybe **quietplease** could give more answers.

---

### Post by gabzelos on 2011-04-17
hello 

i am new in linux and i am trying to have 64bit  apps like autocad 2012 64bit on wine64. well in any application after running this script i cannot run the .exe file. is wine installed on my ubuntu or i have to install it again. help me please i am trying too hard...

thank you

---

