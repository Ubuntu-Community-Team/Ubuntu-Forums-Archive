---
title: "How To Install .tar.gz?"
date: 2010-01-19
forum: General Help
---

### Post by joelandsonja on 2010-01-19
I realize this topic has been on the forum MANY times, but I have yet to find a solution to my problems. 
 
Here's the problem, I am trying to install the latest version of K9copy, but the only available version is in the .tar.gz file package.
 
I placed the folder on my desktop and extracted the files. 
 
Now I have the .tar.gz file and the extracted files on the desktop.
 
I need to install the files, but I don't know which command to use or what to do to get any commands to work. 
 
(Keep in mind that the extracted folder is named 'k9copy-2.3.4-Source.tar.gz')

> ./configure
make
make install

This seems to be the most common answer to install the files, but it NEVER works, nor do I understand where the package files come into play when I type this command into the terminal. 
 
I am a newbie folks, so please don't assume that I know what you are talking about if you say "Just input this command and it should install". 
 
I would really appreciate it if someone please give me step by step instructions on how to install this file ...
 
Thanks for the help!

---

### Post by wojox on 2010-01-19
Did you read the README or INSTALL file that should have came with it.

Why doesn't ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package

make will compile all the source files into executable binaries.

make install will install the binaries and any supporting files into the appropriate locations.
 

They should all be run with sudo.

---

### Post by Simian Man on 2010-01-19
There is no uniform way to install tar.gz files, because there could be anything inside of them.  If it's compiled programs (unlikely) you may have to move it somewhere convenient manually or run an installation script if there is one.

If it's source code (likely), then you will have to compile and install it yourself.  This is often done with the ./configure, make, make install process, but there are other ways to build software too.  Also you will need to install the dependencies needed to build and run the software.

Read the INSTALL, README or any other file that looks helpful for directions.  If those directions don't work or don't make sense, post back.

> **wojox said:**
> Why doesn't ./configure will configure the software to ensure your system has the necessary functionality and libraries to successfully compile the package

make will compile all the source files into executable binaries.

make install will install the binaries and any supporting files into the appropriate locations.
 

They should all be run with sudo.

You should not run configure or make with root privileges.  Only the last step needs that!  Why would you need to be root to compile something?

---

### Post by tom4everitt on 2010-01-19
What you have to do before you execute the commands (./configure, make, make install) is to enter the folder that you extracted. 

Extract the folder in your home folder. 

Open a terminal. 

Write 'cd <name-of-extracted-folder>' (its case sensitive).

Then run ./configure.

Then run make

Then run sudo make install.

---

### Post by wojox on 2010-01-19
> **Simian Man said:**
> 
You should not run configure or make with root privileges.  Only the last step needs that!  Why would you need to be root to compile something?

Stand corrected. Your right. ;)

---

### Post by tom4everitt on 2010-01-19
I downloaded the package and this is not a case for the ./configure-make procedure.

---

### Post by scouser73 on 2010-01-19
Why not just use the Synaptic Package Manager to search for and install K9Copy, or use the Terminal and type **> sudo apt-get install k9copy**

---

### Post by Simian Man on 2010-01-19
Ah I downloaded and see that it's built using cmake which is an alternative build system.  The way it works is it generates other build scripts for you to use such as makefiles.  I haven't used cmake before, but if you navigate to the k9copy directory and run "cmake ." it should either give you some error or produce a makefile for you.  You will have to install cmake first.

When I tried it, it complained about KDE libs missing but I'm *not* going to install them to help you :)

---

### Post by aysiu on 2010-01-19
Maybe the Debian K9Copy .deb would work?
[http://debian-multimedia.org/pool/main/k/k9copy/k9copy_2.3.4-0.1_i386.deb](http://debian-multimedia.org/pool/main/k/k9copy/k9copy_2.3.4-0.1_i386.deb)

I think whether you compile from source or use a package, you'll still end up with dependency errors if you want to install the absolute latest version.

---

### Post by mc4man on 2010-01-19
Basically you'd run this at your extracted source prompt
```
cmake ./
```
That will check if you have the proper build dep.'s and if so create the makefiles. (worth reading thru no matter what

If successful than follow with
make

It appears you can also do a checkinstall, if so you must rename the extracted source dir. to remove the -source (k9copy-2.3.4

With something like k9 you'd need to run it to make sure all is well, A successful build and install isn't 100% assured of it working properly (though at first glance all seems fine

> Done. The new package has been installed and saved to

 /home/doug/Downloads/k9copy-2.3.4/k9copy_2.3.4-1_i386.deb

 You can remove it from your system anytime using: 

      dpkg -r k9copy



---

### Post by joelandsonja on 2010-01-19
Thanks for all the help folks, but I still can't get this to work. 

I downloaded the newest version of k9copy.deb, but I got the following error message when I tried installing it. 

"Error: Dependency is not satisfiable: kdelibs5 (>= 4:4.3.4)" 

I downloaded the latest kdelibs5, but it didn't fix the problem. * Edit - Actually I just checked, and it seems the package available on Synaptic is 4:4.3.2 ... now I suppose I have to find this .deb package?

I don't think K9copy was meant to work on my system, because nothing seems to want to fix it. I may end up doing a complete format of my harddrive and starting from scratch. 

This is frustrating to say the least.

---

### Post by dannyboy79 on 2010-01-19
k9copy (or any source code meant for i386 (32bit) architecture) can be run on any i386 (32bit) system with the correct libraries and dependencies installed. the problem is that you just want it to work without much hassle, without havnig to do all that legwork. if that's the case then you'll have to use a pre-created .deb like suggested or try to search aptitude with this:

sudo aptitude search k9copy

or even open synaptic, make sure all your repo's are enabled, then use the search function.

good luck

---

### Post by mc4man on 2010-01-19
You cannot use the version from debian-multimedia in karmic.
There are several dependencies where you won't meet the version number 
(actually thru karmic backports you can upgrade to the kdelibs5 version required but there are several qt4* that you will not be able to.

If you were inclined, the straight build as previously described worked out fine, just a matter of** having the proper build-deps** ( and the run deps, which if you install, then remove the karmic k9, will then be satisfied
 

With a little more effort (and patience), what works best is to use the debian-multimedia source, .diff, and .dsc and build a proper debian k9copy package.
(have it done and running now, works just fine

Can be described, and once you get the idea is extremely simple to do. (though the straight make, checkinstall is a bit easier to initially set up and do

---

### Post by dannyboy79 on 2010-01-20
> **mc4man said:**
> You cannot use the version from debian-multimedia in karmic.
There are several dependencies where you won't meet the version number 
(actually thru karmic backports you can upgrade to the kdelibs5 version required but there are several qt4* that you will not be able to.

If you were inclined, the straight build as previously described worked out fine, just a matter of** having the proper build-deps** ( and the run deps, which if you install, then remove the karmic k9, will then be satisfied
 

With a little more effort (and patience), what works best is to use the debian-multimedia source, .diff, and .dsc and build a proper debian k9copy package.
(have it done and running now, works just fine

Can be described, and once you get the idea is extremely simple to do. (though the straight make, checkinstall is a bit easier to initially set up and do

if you're saying that you have a .deb of k9copy that works for karmic and installs all the correct dependencies, then why don't you create a ppa for it or at least post a link to it (there are many locations you could host it)

---

### Post by mc4man on 2010-01-20
> then why don't you create a ppa for it or at least post a link to 
several reasons, the least of which is that particular .deb was built specific to my install and may not work elsewhere. ( plus some libs were static and represent a dist. issue.

Better to build one's self, though while on a live cd  awhile ago did build a .deb that should be good for a standard karmic install. (maybe I'll upload to my mediafire, would want to test first.

As a simplified build either using make install, checkinstall, or as a debian, did this on the live cd, took about 15 - 20 min. 

- for Karmic (Atm probably also Lucid) stock installs
(if you have a static ffmpeg build you may want to temporally remove it, or the libavformat-dev from the build depends, figure it out...

You could either use the source from d-m or from k9 site. (atm same

If from k9 site after extracting to the k9build folder, if the name has -source appended to it than rename to just k9copy-2.3.4, pick up at "cd k9copy-2.3.4"

build deps ( has some extra for debian), **enable backports first **from System -> Admin... -> Updates, and click close -> reload (disable afterwards

```
sudo apt-get install debhelper cmake kdelibs5-dev libxine-dev libdvdread-dev \
libqt4-opengl-dev libmpeg2-4-dev quilt dpkg-dev  pkg-kde-tools \
libdbus-1-dev libhal-dev libhal-storage-dev libxss-dev cdbs libavformat-dev

```

If doing checkinstall install this also 
```
sudo apt-get install checkinstall
```

EDIT:
note that while the debian package will install any missing install/runtime dependencies, the checkinstall or make install **will not.**
If you haven't previously installed the repo k9copy then do so first, it will fill those in for you. Then remove and proceed.

To start
```
mkdir k9build && cd k9build 

```

Get source from d-m, wget is good till ver.updates, or get from k9 site instead - and skip  next 2 commands

```
wget http://debian-multimedia.org/pool/main/k/k9copy/k9copy_2.3.4.orig.tar.gz
```

```
tar xzvf k9copy_2.3.4.orig.tar.gz
```

```
cd k9copy-2.3.4
```

For debian build download attached .diff (r. click - 'save link as') and place in the k9build folder as is ( not in the k9copy-2.3.4 folder) and run next 2, for chk. install skip to "For a make install ..."


```
zcat ~/k9build/k9copy_2.3.4-0ubuntu1.diff.gz |patch -p1 

```
```
chmod +x ./debian/rules
```

For debian build run

```
dpkg-buildpackage -rfakeroot -D -us -uc

```
When done install the .deb in the k9build folder

For a make install or checkinstall run
```
cmake ./ && make
```
when done either 
```
sudo make install
```
or 
```
sudo checkinstall --backup=no --deldoc=yes --deldesc=yes --delspec=yes --default
```

and just in case
```
sudo ldconfig
```

---

### Post by JosephBus1 on 2011-07-06
MeToo ...Thx 4 all Ur help, BUT STILL can't get this to work...I'm in Lucid...In the suggestion to try 

'cmake ./'   

 I'm getting:
 =================================
jg@jg-dsktp:~/bmpx-0.20pre2$     cmake ./

CMake Error: The source directory "/home/jg/bmpx-0.20pre2" does not appear to contain CMakeLists.txt.

Specify --help for usage, or press the help button on the CMake GUI.

jg@jg-dsktp:~/bmpx-0.20pre2$ 
 =================================
Thx,

---

### Post by dannyboy79 on 2011-07-08
> **JosephBus1 said:**
> MeToo ...Thx 4 all Ur help, BUT STILL can't get this to work...I'm in Lucid...In the suggestion to try 

'cmake ./'   

 I'm getting:
 =================================
jg@jg-dsktp:~/bmpx-0.20pre2$     cmake ./

CMake Error: The source directory "/home/jg/bmpx-0.20pre2" does not appear to contain CMakeLists.txt.

Specify --help for usage, or press the help button on the CMake GUI.

jg@jg-dsktp:~/bmpx-0.20pre2$ 
 =================================
Thx,

first of all, what program is this supposed .tar.gz file of? not all .tar.gz source archives are installed the same way. once you extract it with 
```
tar xzvf foo.tar.gz
```
you would cd to the extracted directory and read the normally available README file to see how the source code needs to be installed. Good luck

---

