---
title: "Newbie help on gcc installation"
date: 2010-03-05
forum: General Help
---

### Post by daytripper1021 on 2010-03-05
Hi there.
 
I've a Ubuntu 9.10 linux installed by my officemate on one of our servers. Since he used a CD installation, everytime I would download a package from the 'net the system keeps on searching for the drive.
 
So anyway, I downloaded gcc-4.4.3 since the other packages I wanted to install was looking for a compiler. When I ran ./configure on gcc-4.4.3 this came out:
 
root@RPBox:~/gcc-4.4.3# ./configure
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking target system type... i686-pc-linux-gnu
checking for a BSD-compatible install... /usr/bin/install -c
checking whether ln works... yes
checking whether ln -s works... yes
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: in `/root/gcc-4.4.3':
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
 
It's funny that I'm installing gcc but I can't since it's looking for gcc. :D
 
Hope you can help.
 
Thanks.

---

### Post by darolu on 2010-03-05
Install it from the repositories, I recommend installing the build-essential package, it comes with gcc and more, open a terminal and run:
```
$ apt-get install build-essential
```

You can edit your software sources to take the CD option out and enable online repositories (assuimng you have internet access from that computer) at System - Administration - Software Sources or manually editing your /etc/apt/sources.list file. You can also look for the packages at: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by daytripper1021 on 2010-03-05
> **darolu said:**
> Install it from the repositories, I recommend installing the build-essential package, it comes with gcc and more, open a terminal and run:
```
$ apt-get install build-essential
```
 
You can edit your software sources to take the CD option out and enable online repositories (assuimng you have internet access from that computer) at System - Administration - Software Sources or manually editing your /etc/apt/sources.list file. You can also look for the packages at: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)
 
Hi. I tried doing the apt-get you mentioned but I still ended up with th server looking for the package in the cdrom:
 
[EMAIL="root@RPBox:~/gcc-4.4.3"]root@RPBox:~/gcc-4.4.3[/EMAIL]# apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential

I edited the sources.list file but the cdrom lines are already commented. What else should I do?

---

### Post by darolu on 2010-03-05
Did you run apt-get update first?

---

### Post by daytripper1021 on 2010-03-05
> **darolu said:**
> Did you run apt-get update first?
 
Yes I did but since I don't have an internet/proxy connection setup yet, it fails.

---

### Post by darolu on 2010-03-05
Without internet you can't do much; search for all the packages you need at: [http://packages.ubuntu.com](http://packages.ubuntu.com) download the .deb files and copy them using a pendrive (if you have physical access to the actual machine), if you don't have access to it you can transfer the files via local network if network is functional.

---

### Post by daytripper1021 on 2010-03-05
> **darolu said:**
> Without internet you can't do much; search for all the packages you need at: [http://packages.ubuntu.com](http://packages.ubuntu.com) download the .deb files and copy them using a pendrive (if you have physical access to the actual machine), if you don't have access to it you can transfer the files via local network if network is functional.
 
Darolu hi. That's what I did (see beginning of this thread). I downloaded the gcc package and tried to install it but got the error that it's looking for a C compiler when in fact the gcc is THE C compiler that I wanted to install in the first place.
 
hope you can help. :D

---

### Post by darolu on 2010-03-05
Oh I see, the way you put it made me believe you had downloaded the actual source code :p, what you need to do, is download all the "Red marked" items, as they are dependencies needed for each package.
For example, this link will get you to the GCC package: [http://packages.ubuntu.com/karmic/gcc](http://packages.ubuntu.com/karmic/gcc)

This two items are marked in red:
```
cpp (>= 4:4.4.1-1ubuntu2)
The GNU C preprocessor (cpp)
gcc-4.4 (>= 4.4.1-1)
The GNU C compiler
```
So you need to download and install them first.
You can also download the distro .iso file, mount it and add it to your sources :P

---

### Post by daytripper1021 on 2010-03-08
> **darolu said:**
> Oh I see, the way you put it made me believe you had downloaded the actual source code :p, what you need to do, is download all the "Red marked" items, as they are dependencies needed for each package.
For example, this link will get you to the GCC package: [http://packages.ubuntu.com/karmic/gcc](http://packages.ubuntu.com/karmic/gcc)
 
This two items are marked in red:
```
cpp (>= 4:4.4.1-1ubuntu2)
The GNU C preprocessor (cpp)
gcc-4.4 (>= 4.4.1-1)
The GNU C compiler
```
So you need to download and install them first.
You can also download the distro .iso file, mount it and add it to your sources :P
 
sorry I'm really new at this. how do I mount a .iso file and add to my sources in ubuntu?

---

### Post by daytripper1021 on 2010-03-09
Hi. So here's what happened since the last post above:
 
I downloaded the ubuntu server 9.10 iso file and successfully mounted it on /media/cdrom via this command:
 
mount -o loop -t iso9660 /c0re/temp/ubuntu-9.10-server-amd64.iso /media/cdrom
 
but when I try "sudo apt-get install build-essential" I still got the error below:
 
[EMAIL="root@RPBox:~/gcc-4.4.3"]root@RPBox:~/gcc-4.4.3[/EMAIL]# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential

really need your help on this guys. 
 
Thanks.

---

### Post by d3v1150m471c on 2010-03-09
Correct me if I'm wrong but I think gcc comes with the binutils package in the repos.

---

### Post by daytripper1021 on 2010-03-09
> **daytripper1021 said:**
> Hi. So here's what happened since the last post above:
 
I downloaded the ubuntu server 9.10 iso file and successfully mounted it on /media/cdrom via this command:
 
mount -o loop -t iso9660 /c0re/temp/ubuntu-9.10-server-amd64.iso /media/cdrom
 
but when I try "sudo apt-get install build-essential" I still got the error below:
 
root@RPBox:~/gcc-4.4.3# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package build-essential
 
really need your help on this guys. 
 
Thanks.
 
fresh update: I edited the /etc/apt/sources.list to uncomment the cdrom lines. The command "apt-get update" worked!
 
However, running "sudo apt-get install build-essential" was still nok. It kept on looking for a CD labeled as below:
 
[EMAIL="root@RPBox:/"]root@RPBox:/[/EMAIL]# sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  binutils dpkg-dev fakeroot g++ g++-4.4 gcc gcc-4.4 libc-dev-bin libc6-dev
  libgomp1 libstdc++6-4.4-dev linux-libc-dev
Suggested packages:
  binutils-doc debian-keyring debian-maintainers g++-multilib g++-4.4-multilib
  gcc-4.4-doc libstdc++6-4.4-dbg gcc-multilib manpages-dev autoconf
  automake1.9 libtool flex bison gdb gcc-doc gcc-4.4-multilib
  libmudflap0-4.4-dev gcc-4.4-locales libgcc1-dbg libgomp1-dbg libmudflap0-dbg
  libcloog-ppl0 libppl-c2 libppl7 glibc-doc libstdc++6-4.4-doc
The following NEW packages will be installed:
  binutils build-essential dpkg-dev fakeroot g++ g++-4.4 gcc gcc-4.4
  libc-dev-bin libc6-dev libgomp1 libstdc++6-4.4-dev linux-libc-dev
0 upgraded, 13 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/17.2MB of archives.
After this operation, 61.6MB of additional disk space will be used.
Do you want to continue [Y/n]? Y
Media change: please insert the disc labeled
 'Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)'
in the drive '/cdrom/' and press enter
[B]Media change: please insert the disc labeled
 'Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)'
[/B]in the drive '/cdrom/' and press enter
^C

Note that, as mentioned previously, I've already downloaded the .iso package and mounted it. 
 
Should I rename the CD-label on the sources.list file? Coz here's what the cdrom lines there say:
 
deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)]/ karmic main restricted
deb cdrom:[Ubuntu-Server 9.10 _Karmic Koala_ - Release i386 (20091027.2)]/ karmic main restricted

But to what should I rename it knowing that I'm using an .iso file?
 
please help. thanks.

---

### Post by daytripper1021 on 2010-03-09
> **d3v1150m471c said:**
> Correct me if I'm wrong but I think gcc comes with the binutils package in the repos.
 
yes that is what i'm trying to do. extract and install gcc from the binutils but I'm having problems doing so.

---

### Post by daytripper1021 on 2010-03-09
well I was able to solve this...FINALLY!
 
I enabled connection to the internet via http-proxy and the packages were downloaded and installed. gcc is now working.
 
thanks!

---

### Post by jao_madn on 2010-10-26
hi 
i have the same problem my system is ubuntu lucyd 10.04.1 server edition, i dont have the gcc installed or is it not installed in default if try to search in my bin and path but no luck. i try to search around manually and find this gcc but it is a directory contain a files called cc1 something like /usr/local/gcc/4.4/cc1 is used it to compile but no luck at all also i used the ccp but again the same problem, do i realy need to install the gcc and must find it in the bin directory when installed. i run the dpkg -l ans found the gcc-4.4.4.1 ubuntu something says it the base compiler but this is the gcc i used that give me no luck.

i dont have connection with the internet how do i installed using source when i dont have the compiler.

hope u can help me.

---

### Post by katykat on 2010-10-28
If you can get to a internet linked Ubuntu get to Synaptic, put gcc in the search bar and checkmark the files you want. Depending on the size your flash drive it can be alot. I'd also search for g++. Put 'compiler' in the bar for more options. Also 'make'. 

Click apply. And look closely. SOMEWHERE at the bottom of the popup screen there should be an option to DOWNLOAD ONLY. Check it. And continue. 

Then look in /var/cache/apt/archives/

The files will be there.

Move to flash drive, copy to your system. 

Install wiith gdebi. Better than apt. 

(However if it is from a differernt version you may need to use:
dpkg -i --force-all package.deb . Make backup of /lib and /usr/lib first...)

---

