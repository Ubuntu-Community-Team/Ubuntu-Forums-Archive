---
title: "Installing a file - getting stuck"
date: 2012-09-15
forum: General Help
---

### Post by IAMTubby on 2012-09-15
Hello,
I'm getting stuck while trying to install VLC from the .tar.xz file found in [http://www.videolan.org/vlc/download-sources.html.]("http://www.videolan.org/vlc/download-sources.html.")

These are the steps I found from the internet
1)tar Jxvf <name_of_.tar.xz file>
2)cd into_the_folder_created
3)./configure
This checks if all the required packages/softwares/libraries/frameworks are present in the system.
These are collectively called dependancies right? Correct me if I'm wrong.
For me, when I do this step, it says
```

configure: error: No package 'dbus-1' found.

``` 
I tried doing ```
sudo apt-get install dbus-1
```, but it says ```
E: Unable to locate package dbus-1
```.

I'm stuck. What next ?
4)Typically, you are supposed to do these steps next right ?
make clean
make
But for me it says ```
make: *** No targets specified and no makefile found.  Stop.
```
5)make install
It says```
make: *** No rule to make target `install'.  Stop.

```

How do I proceed ? Please advise.

---

### Post by oldfred on 2012-09-15
There are multiple ways to install software in Linux.

The easiest and best way is to use the repository. Most software is available in the repository and has been verified to work with Ubuntu. 

You can install from Software Center, from synaptic (now you also have to install synaptic), and from command line. 

#refresh
apt-get update #resync package index
apt-get upgrade #newest versions of all packages, update must be run first

sudo apt-get install vlc

If you want to use synaptic

sudo apt-get install synaptic

Then you can use synaptic as a menu choice.

Only if you cannot find software in the repository then you should look for a .deb and the last choice would be to download, compile & install an application.

---

### Post by IAMTubby on 2012-09-15
Thanks for the reply Sir.
Hmm.. but I wouldn't like to install it that way.
In fact, I just uninstalled my vlc, so that I could install it this way.
Please can you help me in this direction. Thanks.

---

### Post by Bucky Ball on 2012-09-15
Are you in the correct directory when you are untarring the file? Sounds obvious but ...

---

### Post by IAMTubby on 2012-09-15
> **Bucky Ball said:**
> Are you in the correct directory when you are untarring the file? Sounds obvious but ...
When I untarred, a folder called vlc-2.0.3 was created. I cd'ed into that folder. Isn't that correct ?
The trouble starts in ./configure.

---

### Post by spjackson on 2012-09-15
There's no point trying to "make" when configure has failed. configure's job is to create the Makefile. If configure fails to create the Makefile, make won't work without one.

A big difference between installing pre-built packages and compiling yourself is that the latter method often requires the development packages (e.g. C/C++ headers) of dependencies, rather than just the runtime package (e.g. shared libraries).

From your error message, it looks like you need libdbus-1-dev. I don't know what else you might need because I've never built vlc, nor read the instructions for doing so.

---

### Post by oldfred on 2012-09-15
Some like to compile & install their own software. Then then may get a newer version, but are testing as new version may not work with older parts in Ubuntu.

Current version in 12.04 is vlc (2.0.3-0ubuntu0.12.04.1) .

---

### Post by IAMTubby on 2012-09-15
> **spjackson said:**
> 
From your error message, it looks like you need libdbus-1-dev. I don't know what else you might need because I've never built vlc, nor read the instructions for doing so.
Thanks for that. Yes this was able to run ./configure for a longer while, but next error it says
```

configure: error: Could not find lua.

```
I tried doing ```
sudo apt-get install lua-devel.x86_64
``` but it says ```
E: Unable to locate package lua-devel.x86_64

```

Will you be able to give the exact name of the package to install like last time ?
Thanks.

---

### Post by IAMTubby on 2012-09-15
Ok, I shall try the steps mentioned in 
[http://www.lua.org/faq.html]("http://www.lua.org/faq.html")

---

### Post by spjackson on 2012-09-15
> **IAMTubby said:**
> 
```

configure: error: Could not find lua.

```I tried doing ```
sudo apt-get install lua-devel.x86_64
``` but it says ```
E: Unable to locate package lua-devel.x86_64

```Will you be able to give the exact name of the package to install like last time ?

liblua5.1-0-dev

---

### Post by oldos2er on 2012-09-16
Try ```
sudo apt-get build-dep vlc
``` which should get most of the dependencies for you.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

---

### Post by IAMTubby on 2012-09-17
> **oldos2er said:**
> Try ```
sudo apt-get build-dep vlc
``` which should get most of the dependencies for you.

Thanks a lot oldos2er for that. I had seen that somewhere, but since I'm new to linux, I want to learn the process, instead of getting the final output. This is the first real software I'm compiling from code. I've heard people saying it'll get easier once you have compiled a couple of sources. But I appreciate your reply sir, and will try it out, if I'm still stuck for a few more days.

> **spjackson said:**
> liblua5.1-0-dev
I got that done spjackson,but now I'm having problems installing madlib.
This is what ./configure says
```

configure: error: Could not find libmad on your system: you may get it from http://www.underbit.com/products/mad/. Alternatively you can use --disable-mad to disable the mad plugin.

```

My attempt:
I went to [http://sourceforge.net/projects/mad/files/libmad/0.15.0b/](http://sourceforge.net/projects/mad/files/libmad/0.15.0b/) and downloaded the libmad-0.15.1b.tar.gz file. But when I say make, it gives me the following error :
```

cc1: error: unrecognized command line option '-fforce-mem'
make[2]: *** [version.lo] Error 1
make[2]: Leaving directory `/home/aftab/Desktop/libmad-0.15.1b'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aftab/Desktop/libmad-0.15.1b'
make: *** [all] Error 2

``` 

I also tried doing this.
Got the madlib rpm package from [https://github.com/madlib/madlib/wiki/Installation-Guide]("https://github.com/madlib/madlib/wiki/Installation-Guide"), converted it to .deb using alien and tried installing using ```
sudo dpkg -i madlib_0.4-2_amd64.deb 
```. What next ? Doesn't that install, or do you have to do something more?
When I go and do a ./configure in the vlc, it again says ```
configure: error: Could not find libmad on your system:
```

Please advise.
 Thanks.

---

### Post by Bucky Ball on 2012-09-17
> **IAMTubby said:**
>  But I appreciate your reply sir

While your manners are commendable, I believe oldos2er might be a woman. ;)

---

### Post by spjackson on 2012-09-17
> **IAMTubby said:**
> 
I also tried doing this.
Got the madlib rpm package from [https://github.com/madlib/madlib/wiki/Installation-Guide]("https://github.com/madlib/madlib/wiki/Installation-Guide"), converted it to .deb using alien and tried installing using ```
sudo dpkg -i madlib_0.4-2_amd64.deb 
```. What next ? Doesn't that install, or do you have to do something more?
When I go and do a ./configure in the vlc, it again says ```
configure: error: Could not find libmad on your system:
```

I'm puzzled about why you choose to make life so much more difficult for yourself than you need to. I'm afraid I don't understand why you won't install libmad0 from the Ubuntu repository but you will use an .rpm. However, if you do install libmad0 from the repository, you'll have the same problem as you have with the above .rpm, i.e. it isn't enough for compiling.

Earlier, I wrote:
> 
A big difference between installing pre-built packages and compiling yourself is that the latter method often requires the development packages (e.g. C/C++ headers) of dependencies, rather than just the runtime package (e.g. shared libraries).

Did you not understand what that means? In this case, it means that you need libmad0-dev in addition to libmad0. Better yet, use apt-get build-dep as advised by oldos2er (I had forgotten about that).

Given this error message:
> 
Could not find libmad on your system

If you google "ubuntu package libmad precise", the first page found is [https://launchpad.net/ubuntu/+source/libmad]("https://launchpad.net/ubuntu/+source/libmad") and that tells you the name of both the runtime and development packages.

---

### Post by IAMTubby on 2012-09-17
> **spjackson said:**
> I'm puzzled about why you choose to make life so much more difficult for yourself than you need to. I'm afraid I don't understand why you won't install libmad0 from the Ubuntu repository but you will use an .rpm. However, if you do install libmad0 from the repository, you'll have the same problem as you have with the above .rpm, i.e. it isn't enough for compiling.

Earlier, I wrote:

Did you not understand what that means? In this case, it means that you need libmad0-dev in addition to libmad0. Better yet, use apt-get build-dep as advised by oldos2er (I had forgotten about that).

Given this error message:

If you google "ubuntu package libmad precise", the first page found is [https://launchpad.net/ubuntu/+source/libmad]("https://launchpad.net/ubuntu/+source/libmad") and that tells you the name of both the runtime and development packages.
Sir, I currently don't have access to an appropriate machine, shall try out and let you know in a few hours.

Thanks.

---

### Post by IAMTubby on 2012-09-17
> **oldos2er said:**
> Try ```
sudo apt-get build-dep vlc
``` which should get most of the dependencies for you.

[https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)
Madam,
I'm sorry for referring to you as "Sir" on another post. I should have noticed your signature.

> **Bucky Ball said:**
> While your manners are commendable, I believe oldos2er might be a woman. ;)
Thanks BuckyBall for pointing it out.


About ```
sudo apt-get build-dep vlc
```, I shall try it out get back to you in a few hours. Currently away from an appropriate machine.

Thanks :)

---

### Post by oldos2er on 2012-09-17
> **IAMTubby said:**
> Madam,
I'm sorry for referring to you as "Sir" on another post. I should have noticed your signature.

Thanks, but we're pretty informal here. No real need for either sir or madam.

---

### Post by IAMTubby on 2012-09-23
Hey, 
I have managed to get a bit further, my ./configure is now working and I have installed all the dependancies. But I have a problem.

I installed a package called 'lua' (lua 5.2.1) but because of some compatibility issues, I now understand that what I actually need is lua 5.1.5. How do I downgrade the package

1. I downloaded the tarball lua-5.1.5.tar.gz and installed it successfully
```

wget http://www.lua.org/ftp/lua-5.1.5.tar.gz
tar zxf lua-5.1.5.tar.gz
cd lua-5.1.5/
make linux test

```

But still the change is not showing any effec. When I do 'make',  it is 5.2.1 which is again getting compiled.

2. So I thought of doing a sudo apt-get remove lua and then installing again, but it says
```

Virtual packages like 'lua' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded

```

Please advise.
Thanks.

---

### Post by spjackson on 2012-09-24
> **IAMTubby said:**
> Hey, 
I have managed to get a bit further, my ./configure is now working and I have installed all the dependancies. But I have a problem.

I installed a package called 'lua' (lua 5.2.1) but because of some compatibility issues, I now understand that what I actually need is lua 5.1.5. How do I downgrade the package

1. I downloaded the tarball lua-5.1.5.tar.gz and installed it successfully
```

wget http://www.lua.org/ftp/lua-5.1.5.tar.gz
tar zxf lua-5.1.5.tar.gz
cd lua-5.1.5/
make linux test

```

But still the change is not showing any effec. When I do 'make',  it is 5.2.1 which is again getting compiled.
 Did this actually install it anywhere? Don't you need to do ```
sudo make install
``` for that?

Where has it been installed? In /usr/local/... ? Wherever it is, if it's not installed via the packaging system, you may need to tell ./configure where to find it.

> 
2. So I thought of doing a sudo apt-get remove lua and then installing again, but it says
```

Virtual packages like 'lua' can't be removed
0 upgraded, 0 newly installed, 0 to remove and 7 not upgraded

```

The package to remove is probably lua5.2 [http://packages.ubuntu.com/precise/lua5.2]("http://packages.ubuntu.com/precise/lua5.2")
It appears that lua5.1 can also be installed from the repositories [http://packages.ubuntu.com/precise/lua5.1]("http://packages.ubuntu.com/precise/lua5.1")

---

### Post by andrew.46 on 2012-11-12
I have a web page that illustrates how to compile the *development* version of vlc for Quantal, perhaps this might give you a start? You would be best to modify the guide to compile the release version rather than the cutting edge, unreleased version:

Howto: Build the development version of vlc under Ubuntu
[http://www.andrews-corner.org/vlc.html](http://www.andrews-corner.org/vlc.html)

This guide should show you how to assemble the appropriate compiling tools, required dependencies and also give an idea of how to set up suitable ./configure and packaging options.

---

### Post by IAMTubby on 2012-11-12
> **andrew.46 said:**
> I have a web page that illustrates how to compile the *development* version of vlc for Quantal
Thanks a lot Andrew, can I try and get back to you in a few days, currently caught up with something.

---

### Post by andrew.46 on 2012-11-13
> **IAMTubby said:**
> Thanks a lot Andrew, can I try and get back to you in a few days, currently caught up with something.

The web page will still be there :).

---

