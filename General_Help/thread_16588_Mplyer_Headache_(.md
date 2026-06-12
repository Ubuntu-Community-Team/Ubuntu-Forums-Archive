---
title: "Mplyer Headache :("
date: 2005-02-22
forum: General Help
---

### Post by bingo11 on 2005-02-22
Thans y'all for the great tips.

I am fairly new to linux and i had a problem trying to install MPlyaer. i was trying to follow the how-to MPLYER posted here :
[http://www.ubuntuforums.org/showthread.php?t=94](http://www.ubuntuforums.org/showthread.php?t=94) 

When i try ./configure --enable-gui ,  i get the following error :

Error: PNG support required for GUI compilation, please install libpng and libpng-dev packages.


I try to get the libpng12-0 and it says that i have the latest version but when trying to "sudo apt-get install libpng12-dev" i get :

------------------------------------------------------------------------------------------------------
The following information may help to resolve the situation:

The following packages have unmet dependencies:
libpng12-dev: Depends: libpng12-0 (= 1.2.5.0-7) but 1.2.5.0-7ubuntu1 is to be installed
E: Broken packages


my /etc/apt/sources.list looks like this 

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ uns$

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
------------------------------------------------------------------------------------------------------

Any help would be highly appreciated

PS: I am a starter so please don't ask me to re-compile a kernel ou reinstall a Glibc 

Madi

---

### Post by kassetra on 2005-02-22
[QUOTE=bingo11]Thans y'all for the great tips.

I am fairly new to linux and i had a problem trying to install MPlyaer. i was trying to follow the how-to MPLYER posted here :
[http://www.ubuntuforums.org/showthread.php?t=94]("http://www.ubuntuforums.org/showthread.php?t=94") 

When i try ./configure --enable-gui ,  i get the following error :

Error: PNG support required for GUI compilation, please install libpng and libpng-dev packages.


I try to get the libpng12-0 and it says that i have the latest version but when trying to "sudo apt-get install libpng12-dev" i get :

------------------------------------------------------------------------------------------------------
The following information may help to resolve the situation:

The following packages have unmet dependencies:
libpng12-dev: Depends: libpng12-0 (= 1.2.5.0-7) but 1.2.5.0-7ubuntu1 is to be installed
E: Broken packages


my /etc/apt/sources.list looks like this 

deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ uns$

deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") warty universe
deb-src [http://archive.ubuntu.com/ubuntu]("http://archive.ubuntu.com/ubuntu") warty universe

deb [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu]("http://security.ubuntu.com/ubuntu") warty-security main restricted
------------------------------------------------------------------------------------------------------

Any help would be highly appreciated

PS: I am a starter so please don't ask me to re-compile a kernel ou reinstall a Glibc 

Madi[/QUOTE]

Ok, first of all have you tried using Synaptic?  It might be more helpful than the command line in this case:
Computer->System Configuration->Synaptic Package Manager

The reason I'm suggesting Synaptic is that you'll be able to "see" your libpng files, and know exactly which one is installed... You can do a search for "png" and then see what synaptic shows...  Also if you try to install libpng-dev from synaptic, it might give you more information about what it needs/what's wrong...

Also, is there any reason you want mplayer over xine?  If you just prefer it that's cool, I can help you get it all installed.  :)

---

### Post by WillCooke on 2005-02-22
You don't mention this, so I'll assume you haven't tried it:

sudo apt-get update

Then try again/.
If you've already tried this, sorry.

---

### Post by bingo11 on 2005-02-22
I got it right this time... :)

What i did is edited my sources.list to look like this :
deb cdrom:[Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ uns$

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

deb [http://ubuntu-bp.sourceforge.net/ubuntu/](http://ubuntu-bp.sourceforge.net/ubuntu/) warty-backports main universe

Then $ sudo apt-get update
	 $ sudo apt-get upgrade
 	 $ sudo apt-get dist-upgrade

And that seemed to fix it. Now to tell you the truth, i still have no idea what i did here and what could have been the problem. Can any one please explain to me how could modifying my source.lst be related to libpng


Mahdi

---

### Post by kassetra on 2005-02-22
here's how the sources.list file and libpng are related:

Most packages have a dependency list that needs to be installed before you can install the package you want.

In ubuntu, we install packages with apt.  Now, apt can be smart sometimes, and go find the package dependencies you need and install them for you (isn't that nice?) however, you don't want apt going out all over the internet and finding ANY package that meets the dependency requirements and installing it... 

Since we need to limit where apt goes to find dependencies to install, there is a sources.list file - that tells apt you can go here, here, here, and here to find packages.

In your case mplayer needed libpng, but with your current sources.list, apt couldn't find the appropriate package... when you added more sources for apt to look in, it found it and installed everything like it was supposed to.  :)

---

### Post by bingo11 on 2005-02-22
Kassetra,
That was beautifully explained. Thanks for making it clearer.

Madi

---

### Post by nocturn on 2005-02-23
[QUOTE=bingo11]Kassetra,
That was beautifully explained. Thanks for making it clearer.

Madi[/QUOTE]


If you still have problems, I made a package for Mplayer with checkinstall, I can send it to you if you want (PM me).

---

