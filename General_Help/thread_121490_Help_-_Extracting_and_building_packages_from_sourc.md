---
title: "Help - Extracting and building packages from source???"
date: 2006-01-25
forum: General Help
---

### Post by MJSOnline on 2006-01-25
How do i go about extracting and building gutenprint drivers once I have downloaded them?

Thanks in advance.  Matthew

---

### Post by ubuntumaneh on 2006-01-25
what is the name of the file you just downloaded?

Anyway, usually it is a tarball file, with either gz or bz2:
if gz:

tar xzvf name_of_file

if bz2:

tar xjvf name_of_file

then you go to the directory and:

./configure
make
make install

Sometimes there is some problems, like unmet dependencies, and you will have to post it here, or try to see if you know what is lacking and install it.
BTW, check if you have build-essentials installed before going into make part.

good luck

---

### Post by MJSOnline on 2006-01-25
Hi.  Its called "gutenprint-5.0.0-rc1.tar.bz2" for my Epson R300 printer.  I was told to download it and build it, then use it.

Does that help?

What do I need now?
Matthew

---

### Post by ubuntumaneh on 2006-01-25
tar xjvf gutenprint-5.0.0-rc1.tar.bz2

then enter in the directory gutenprinter_something
./configure
make
make install

---

### Post by MJSOnline on 2006-01-25
[QUOTE=ubuntumaneh]tar xjvf gutenprint-5.0.0-rc1.tar.bz2

then enter in the directory gutenprinter_something
./configure
make
make install[/QUOTE]

Hi.  Thanks for the info.  I did that and got this in terminal

tar xjvf gutenprint-5.0.0-rc1.tar.bz2
tar: gutenprint-5.0.0-rc1.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

What does it mean?  What did I do wrong?  does the file I downloaded have to be somewhere else, it is on my 2nd hard drive under a folder.

Thanks again.
Matthew

---

### Post by ubuntumaneh on 2006-01-25
you have to be in the directory of gutenprint file.
A good thing to do is after typed "tar xjvf guten" you press tab to complete it. If there is no completion, you are not in the right directory, or type tab again.

---

### Post by MJSOnline on 2006-01-25
How do I get to my folder then?  Do I have to use teminal?

Matthew

---

### Post by ubuntumaneh on 2006-01-25
Sorry for not telling that. You need to use a terminal. If there is a way to do it using a GUI, Im not aware of, and it would be a nice script.
So, go to terminal. And look for you file.
Maybe, it is in the Desktop directory, try it:

cd Desktop
ls

If you couldn't find it. Try:

sudo updatedb
slocate gutenprint

---

### Post by MJSOnline on 2006-01-25
Ok,  I did that. 

this was the result...

matthew@Main:/media/SlaveDrive/DLoads$ cd gutenprint-5.0.0-rc1

matthew@Main:/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1$ ./configure

checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... no
checking build system type... i686-pc-linuxoldld
checking host system type... i686-pc-linuxoldld
checking for style of include used by make... none
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.
matthew@Main:/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1$

What am I missing?

Matthew

---

### Post by ubuntumaneh on 2006-01-25
do:

sudo apt-get install build-essentials

then try it again:
./configure
make
make install

Maybe there will be still some problems. But we are going to solve all.

---

### Post by ubuntumaneh on 2006-01-25
sorry:
build-essential

---

### Post by MJSOnline on 2006-01-25
Ok.  Did that and got this..

Reading package lists... Done
Building dependency tree... Done
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) breezy-extras/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_breezy-extras_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Couldn't find package build-essentials

I am now pulling my hair out.  I am very new to Ubuntu and Linux.  It scary...

Does it show?  Matthew

---

### Post by ubuntumaneh on 2006-01-25
Keep cool. You are doing something that is not usually trivial. And we are almost there. This build-essential is really very important, and it is a big file. Now, you had problems with your repositories.
Try the following things:

First) 
sudo apt-get update
sudo apt-get install buld-essential

If there is error messages after apt-get update, you will have to change things. Then we go to second thing. I will wait your response.

---

### Post by ubuntumaneh on 2006-01-25
by the way, I have corrected myself, and maybe you haven't seen:

sudo apt-get install build-essential

without the "s". This will make the difference. Sorry, again.

---

### Post by carlosqueso on 2006-01-25
You need to get rid of the mirrormax repositories, they don't work.  Type ```
 sudo gedit /etc/apt/sources.list
``` in a terminal and put a # in front of the ones with mirrormax in the name.  Then I'll turn you back over to ubuntumaneh for the rest of the process.

---

### Post by ubuntumaneh on 2006-01-25
Thanks a lot carlosqueso. That's true. However, if he just correct my mis-spelling of build-essential, I believe it will do. Then this mirrormax issue, he will have to tackle later, using exactly your tip. Im not familiar with synaptics, is there a GUI way to get rid of these mirrormax repositories, and add other ones?

---

### Post by carlosqueso on 2006-01-25
beats me....I use apt for everything unless I don't know the name of the package I'm needing.

---

### Post by MJSOnline on 2006-01-25
Ok guys T did the "#" thing and it worked.

However when I did the "sudo apt-get install build-essential" thing I get the following..

matthew@Main:/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
matthew@Main:/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1$

This is a copy of my sources list
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

## Official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

## PLF - [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free


What is it now?  Thanks for your help, matthew.

---

### Post by ubuntumaneh on 2006-01-25
This is strtange. Please insert the following in your sources.list:

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe

then do:
sudo apt-get update
sudo apt-get install build-essential

---

### Post by MJSOnline on 2006-01-25
Ok. Did the inserts.  A ok on that, but tried the "sudo apt-get install build-essential" and, well see below....

matthew@Main:/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
matthew@Main:/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1$

I am now at a loss.

Matthew

---

### Post by ubuntumaneh on 2006-01-25
Try this, then:
go to synaptic and look for build-essential. Try to install from there. 

Sorry, Im not understand what is going on now. our sources.list seems ok to me. I tried here this very much thing, and it is working. I don´t have synaptic. So after you have installed build-essential from there, we can resume the installation of your pkg.
Im looking forward for your success and comments.

---

### Post by MJSOnline on 2006-01-25
Ok.  Thanks for waiting for me.

Ok into Synaptic > searched and clicked to install > Apply and.....  
sbuild:
 Depends: dpkg-dev  but it is not installable
 Depends: grep-dctrl  but it is not installable

Now, what the hell does that mean??  Can I just copy a good clean copy of a source list to make all this work properly?

Matthew

---

### Post by ubuntumaneh on 2006-01-25
The sources.list below has worked here. Also install manually dpkg-dev and grep-dctrl.

----------------- 


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

---

### Post by MJSOnline on 2006-01-25
[QUOTE=ubuntumaneh]The sources.list below has worked here. Also install manually dpkg-dev and grep-dctrl.

----------------- 


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe[/QUOTE]


So can I just copy all the above and overwrite my sources list file?  Do i have to reboot?  Then do I install "sbuild" from Synaptic?

Many thanks for you help.  Matthew

---

### Post by ubuntumaneh on 2006-01-25
do the following:

cd /etc/apt
sudo cp sources.list sources.lis.OLD
sudo nano sources.list 

then, you copy the above one into that file, then you save:

ctrl+x

NOw:

sudo apt-get update

you don´t have to reboot. Look at synaptcs for build-essential.

---

### Post by MJSOnline on 2006-01-25
Ok.  Sorry aboiut the wait.

The 1st bit worked, thanks for that.  Dont know what you said for me to do, but it worked.  I got to learn this stuff...

The 2nd part gave this message... via synaptic.

sbuild:
 Depends: dpkg-dev  but it is not installable
 Depends: grep-dctrl  but it is not installable

What it is.  Can I bypass it?  

Matthew

---

### Post by ubuntumaneh on 2006-01-25
So, now you have build-essential?

To test it, type in terminal:
dpkg -l | grep build-esse

If the output is a line beggining with ii, followed by the name of pkg, build-essential, then we have done it. Congratulations.

Now, resuming. Go to that directory, where there is the gutenprint and type:
./configure
make
make install

Maybe ou have to do it with sudo, due to the directory you are.

---

### Post by MJSOnline on 2006-01-25
Er.. Nope.  No joy at all.

I am pulling my hair out now.  Do I have to reinstall the whole system again?

Matthew

---

### Post by ubuntumaneh on 2006-01-25
Try this in terminal, then:
sudo apt-get install dpkg-dev grep-dctrl

or try to install these twwo in synaptic. Then go for build-essential.

---

### Post by lupine_nickt on 2006-01-25
I have never -ever - installed this "build-essentials" thingy, but I can build packages.

If you can't install it for whatever reason, try "apt-get install gcc g++ make binutils" in the terminal. The error message you got when trying to compile (back on page 1 or whatever ;) ) was telling you that you didn't have a C compiler - installing GCC (the first term) would sort that for you... the rest are all other programs it's likely to want installing.

Then you do ./configure again, and (fingers crossed) it'll complete. (what the configure script does, is checks for the location of various programs, libraries, etc that make wil need to build the program). 

Most likely, it'll fail and say 'Checking for <x>.... no' - in which case, you plug in 'apt-get install <x>' (or appropriate derivatives), and ./configure again - until you get success. I'm around 'til 10, so if you give it a blast and come up against any packages you can't find, feel free to post & I'll try to help... :)

xF,
...Nick

---

### Post by MJSOnline on 2006-01-25
Hi Nick..
I trried that "apt-get install gcc g++ make binutils" and got this message...

matthew@Main:~$ apt-get install gcc g++ make binutils
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
matthew@Main:~$

Any help?
Matthew

---

### Post by ubuntumaneh on 2006-01-26
You have forgotten to write sudo before the apt-get command. Try this:

sudo apt-get install gcc g++ make binutils

---

### Post by MJSOnline on 2006-01-27
Ok,  I did that, and still got this....

[B]matthew@Main:~$ sudo apt-get install gcc g++ make binutils
Password:
Reading package lists... Done
Building dependency tree... Done
Package gcc is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
  gcc272-docs gcc272 gcc-3.3-doc gcc-2.95-doc g++-2.95
E: Package gcc has no installation candidate
matthew@Main:~$ [/B]

Any more ideas?  Thanks again.. Matthew

---

### Post by ubuntumaneh on 2006-01-27
change again your sources.lis for the one below:

cd /etc/apt
sudo mv sources.list sources.list.bk
sudo nano sources.list

save it.

then:
sudo apt-get update
sudo apt-get install build-essential

---------------------------------------
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse

---

### Post by MJSOnline on 2006-01-27
[QUOTE=ubuntumaneh]change again your sources.lis for the one below:

cd /etc/apt
sudo mv sources.list sources.list.bk
sudo nano sources.list

save it.

then:
sudo apt-get update
sudo apt-get install build-essential

---------------------------------------
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse[/QUOTE]

Ok.  the whole
[B]
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse
#deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted universe multiverse[/B]
?

Ok.  Matthew.  By the what am I doing wrong?

---

### Post by ubuntumaneh on 2006-01-27
The whole thing.

Try it, and then we see.

---

### Post by MJSOnline on 2006-01-27
Er... did that bit and the result is below.  Looking at the message, it does not look good..

[B]matthew@Main:~$ cd /etc/apt
matthew@Main:/etc/apt$ sudo mv sources.list sources.list.bk
mv: cannot stat `sources.list': No such file or directory
matthew@Main:/etc/apt$[/B]

What do you think?  Ok.. from the begining / top? Idiot fashion?  Matthew

---

### Post by ubuntumaneh on 2006-01-27
please, give me the result of:

ls /etc/apt

---

### Post by MJSOnline on 2006-01-27
[QUOTE=ubuntumaneh]please, give me the result of:

ls /etc/apt[/QUOTE]

Ok..

[B]matthew@Main:/etc/apt$ ls /etc/apt
apt.conf.d           sources.list_backup_200601160950  sources.list.save.2
secring.gpg          sources.list_backup_200601251132  trustdb.gpg
sources.lis.OLD      sources.list.bk                   trusted.gpg
sources.list~        sources.list.save                 trusted.gpg~
sources.list_backup  sources.list.save.1
matthew@Main:/etc/apt$[/B]

I am so out of my deapth with this, but I want to try to lean a new system... Matthew

---

### Post by ubuntumaneh on 2006-01-27
Now, I know the problem. You just listed the files in the folder (or directory) /etc/apt/

There is a file called sources.list with those information I sent to you before. Now, this file is missing. SO let's create it.

Type (to open an editor)
sudo nano sources.list

copy that text I sent to you, the whole thing. TIP: to copy and paste, use the mouse. To select, press the left button while marking. To past, just use midlle butto.

After that, you save it with ctrl+x.

Then:
sudo apt-get update
sudo apt-get install build-essential

---

### Post by MJSOnline on 2006-01-27
Did upto saveing it.  Saved it crl x, ok.  Closed it and then did the next step, update and got this...

[B]matthew@Main:~$ sudo apt-get update
E: Opening /etc/apt/sources.list - ifstream::ifstream (2 No such file or directory)
matthew@Main:~$[/B]

Now I am looking at bouncing this base usit out the window...  S***! Matthew

---

### Post by ubuntumaneh on 2006-01-27
"Once more unto the bridge, my fellow"

cd /etc/apt/
sudo mv sources.list.bk sources.list
sudo apt-get update
...


Anyway, perhaps there is a problem with your apt-get. Im googling it. And I will resume it to you.

EDIT: Please, post here the result of:
 
cat /etc/apt/sources.list

---

### Post by MJSOnline on 2006-01-27
Ok.  did the lst post you posted.. and below is the result.

[B]matthew@Main:~$ cd /etc/apt/
matthew@Main:/etc/apt$ sudo mv sources.list.bk sources.list
Password:
matthew@Main:/etc/apt$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:11 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:12 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:13 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 39.6kB in 2s (14.0kB/s)
Reading package lists... Done
matthew@Main:/etc/apt$

[/B]Does that help?  Matthew

and...
[B]
matthew@Main:/etc/apt$ cat /etc/apt/sources.list
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu](http://au.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe multiverse

## Security Updates
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe multiverse

deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted universe

## Official backports
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) breezy-extras main restricted universe multiverse

## PLF - [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
deb-src [ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/](ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/) breezy free non-free
matthew@Main:/etc/apt$[/B]

Matthew

---

### Post by GeneralZod on 2006-01-27
That looks good to me.  Try

```

sudo apt-get install build-essential

```

again.

---

### Post by ubuntumaneh on 2006-01-27
All seems to be working properly now.
Go for:
sudo apt-get install build-essential

Hope it works.

---

### Post by MJSOnline on 2006-01-27
Ok.  Er..

[B]matthew@Main:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
matthew@Main:~$[/B]

For *** sake!  What am I missing?    Matthew

---

### Post by ubuntumaneh on 2006-01-27
Do you have you Breezy installation cd with you?

---

### Post by MJSOnline on 2006-01-27
Yes. DVD version. 
M

---

### Post by ubuntumaneh on 2006-01-27
Ok.

sudo nano /etc/apt/sources.list

Then in the first line you insert the following:
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

then you save again (ctrl+x).

Then:
sudo apt-get update
sudo apt-get install build-essential

P.S.: I don't have dvd-rom, so I think that with cdrom will do in the address. If not, someone could correct me.

---

### Post by MJSOnline on 2006-01-27
Ok. Do i put the DVD in before I do all that?  All in Terminal? M

---

### Post by ubuntumaneh on 2006-01-27
Yes. Insert the dvd. And, yes, type all that in the terminal, as usual.

---

### Post by GeneralZod on 2006-01-27
[QUOTE=MJSOnline]
For *** sake!  What am I missing?    Matthew[/QUOTE]

This is nuts.  I have absolutely no idea what's wrong here.  You shouldn't have to resort to loading it off the DVD.

The only thing I can think of here is that some mirror is down, but the output of sudo apt-get update you gave seems to contradict this.

---

### Post by ubuntumaneh on 2006-01-27
I agree with you General Zod. So if some mirror is down. The dvd will do for the time being, won't it?
But this whole thing is being very weird.

---

### Post by GeneralZod on 2006-01-27
[QUOTE=ubuntumaneh]I agree with you General Zod. So if some mirror is down. The dvd will do for the time being, won't it?
But this whole thing is being very weird.[/QUOTE]

It will do for the time being (I hope!), but it needs to be sorted out for him at some point.  It's all very odd indeed.

OP - try opening up Synaptic again, clicking Reload, and searching for build-essential

---

### Post by MJSOnline on 2006-01-27
[B]matthew@Main:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:10 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:11 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Get:12 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:13 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release [19.6kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Get:14 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Sources
Fetched 59.4kB in 23s (2566B/s)
Reading package lists... Done
matthew@Main:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
Package build-essential is not available, but is referred to by another package.This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package build-essential has no installation candidate
matthew@Main:~$
[/B]

Ok did all that and the result is above.  Will type Synaptic next.  

from synaptic 

[B]sbuild:
 Depends: dpkg-dev  but it is not installable
 Depends: grep-dctrl  but it is not installable[/B]

Checked Synaptic and the only one not installed, i.e. green box, is grep-dctrl.  do i install it?
Hm.... Matthew

---

### Post by ubuntumaneh on 2006-01-27
The dvd was not read. Have you inserted that line:
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted

in your sources.list?

---

### Post by MJSOnline on 2006-01-27
Yes.  Heres the result from terminal

[B]matthew@Main:~$ sudo nano /etc/apt/sources.list
matthew@Main:~$ sudo apt-get update
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release.gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy ReleaseIgn cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release
Get:5 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Get:6 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:8 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Get:9 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Get:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Get:11 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Sources
Fetched 5B in 22s (0B/s)
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/dists/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.
matthew@Main:~$[/B]

Now what does the top bit mean?  Matthew.  The CD/DVD drive did not spin up.  M
Screenshot of the DVD permissions

---

### Post by ubuntumaneh on 2006-01-27
See the good side of it: we are learning.
The message tells us to use this apt-cdrom. I never had to used it before. I read the man page: man apt-cdrom.
First, you have to delete that line of the cdrom in the sources.list. 
Then, apparently, you have to insert the dvd and then type:
sudo apt-cdrom add

---

### Post by MJSOnline on 2006-01-27
This is true. My head hurts tho..
Ok output from terminal is...

[B]matthew@Main:~$ sudo nano /etc/apt/sources.list
Password:
matthew@Main:~$ sudo apt-cdrom add
Using CD-ROM mount point /cdrom/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter
Mounting CD-ROM...
Identifying.. [c367d1545bb0b8959110c9705b941245-2]
Scanning disc for index files..
Found 2 package indexes, 0 source indexes and 1 signatures
This disc is called:
'Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)'
Copying package lists...gpgv: Signature made Wed 12 Oct 2005 19:48:47 BST using DSA key ID FBB75451
gpgv: Good signature from "Ubuntu CD Image Automatic Signing Key <cdimage@ubuntu.com>"
Reading Package Indexes... Done
Writing new source list
Source list entries for this disc are:
deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
Unmounting CD-ROM...Repeat this process for the rest of the CDs in your set.
matthew@Main:~$[/B]

Now is that good? M

---

### Post by ubuntumaneh on 2006-01-27
Very good. Let's proceed all over again:

sudo apt-get update
sudo apt-get install build-essential

---

### Post by MJSOnline on 2006-01-27
Ok.  good. The output from terminal is...
[B]
matthew@Main:~$ sudo apt-get update
Password:
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports Release [19.6kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy-backports/multiverse Sources
Get:6 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Get:7 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release.gpg
Get:8 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:9 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy Release
Get:10 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates Release
Get:11 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Get:12 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Packages
Get:13 [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Ign [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Packages
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [ftp://ftp.free.fr](ftp://ftp.free.fr) breezy/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Sources
Fetched 39.6kB in 22s (1778B/s)
Reading package lists... Done
matthew@Main:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  binutils dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev libstdc++6-4.0-dev
  linux-kernel-headers make
Suggested packages:
  binutils-doc debian-keyring gcc-4.0-doc lib64stdc++6 manpages-dev autoconf
  automake1.9 libtool flex bison gcc-doc gcc-4.0-locales libc6-dev-amd64
  lib64gcc1 glibc-doc libstdc++6-4.0-doc stl-manual
Recommended packages:
  libmudflap0-dev
The following NEW packages will be installed:
  binutils build-essential dpkg-dev g++ g++-4.0 gcc gcc-4.0 libc6-dev
  libstdc++6-4.0-dev linux-kernel-headers make
0 upgraded, 11 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.2MB of archives.
After unpacking 41.9MB of additional disk space will be used.
Do you want to continue [Y/n]? y

Preconfiguring packages ...
Selecting previously deselected package binutils.
(Reading database ... 82800 files and directories currently installed.)
Unpacking binutils (from .../binutils_2.16.1-2ubuntu6_i386.deb) ...
Selecting previously deselected package linux-kernel-headers.
Unpacking linux-kernel-headers (from .../linux-kernel-headers_2.6.11.2-0ubuntu13_i386.deb) ...
Selecting previously deselected package libc6-dev.
Unpacking libc6-dev (from .../libc6-dev_2.3.5-1ubuntu12_i386.deb) ...
Selecting previously deselected package gcc-4.0.
Unpacking gcc-4.0 (from .../gcc-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package gcc.
Unpacking gcc (from .../gcc_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package libstdc++6-4.0-dev.
Unpacking libstdc++6-4.0-dev (from .../libstdc++6-4.0-dev_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++-4.0.
Unpacking g++-4.0 (from .../g++-4.0_4.0.1-4ubuntu9_i386.deb) ...
Selecting previously deselected package g++.
Unpacking g++ (from .../g++_4%3a4.0.1-3_i386.deb) ...
Selecting previously deselected package make.
Unpacking make (from .../archives/make_3.80-9_i386.deb) ...
Selecting previously deselected package dpkg-dev.
Unpacking dpkg-dev (from .../dpkg-dev_1.13.10ubuntu4_all.deb) ...
Selecting previously deselected package build-essential.
Unpacking build-essential (from .../build-essential_11.1_i386.deb) ...
Setting up binutils (2.16.1-2ubuntu6) ...

Setting up linux-kernel-headers (2.6.11.2-0ubuntu13) ...
Setting up libc6-dev (2.3.5-1ubuntu12) ...
Setting up gcc-4.0 (4.0.1-4ubuntu9) ...
Setting up gcc (4.0.1-3) ...

Setting up make (3.80-9) ...

Setting up dpkg-dev (1.13.10ubuntu4) ...
Setting up libstdc++6-4.0-dev (4.0.1-4ubuntu9) ...
Setting up g++-4.0 (4.0.1-4ubuntu9) ...
Setting up g++ (4.0.1-3) ...

Setting up build-essential (11.1) ...
matthew@Main:~$[/B]

Is that good? M

---

### Post by ubuntumaneh on 2006-01-27
Bravo!
That's very good. Now, you can install. Do you remember the commands? Anyway, go to the directory of the gutenprint, then type:
./configure
make
make install

Perhaps, you will have to use sudo, for the directory you are. And be aware that you will have to install other programs to be succesful.

---

### Post by GeneralZod on 2006-01-27
[QUOTE=ubuntumaneh]Bravo!
That's very good. Now, you can install. Do you remember the commands? Anyway, go to the directory of the gutenprint, then type:
./configure
make
make install

Perhaps, you will have to use sudo, for the directory you are. And be aware that you will have to install other programs to be succesful.[/QUOTE]

If these are drivers, won't they need to be compiled as kernel modules? If so, he'll need GCC 3.4....

---

### Post by MJSOnline on 2006-01-27
My ***!!  What went wrong in the 1st place then?  What a **** ache!! How do I lean stuff like that then?

I see there is new book out soon, [http://www.amazon.co.uk/exec/obidos/ASIN/1590596277/qid=1138368074/sr=8-1/ref=sr_8_xs_ap_i1_xgl/026-2515326-6430857]("http://www.amazon.co.uk/exec/obidos/ASIN/1590596277/qid=1138368074/sr=8-1/ref=sr_8_xs_ap_i1_xgl/026-2515326-6430857") Would that help me?  A crash course maybe, or have I just done it?

Many thanks.  Lets see if the package works now.  God help me if my system goes **** up now, I will have to do it all again, mounting disks, network printers etc....
M

---

### Post by MJSOnline on 2006-01-27
[QUOTE=GeneralZod]If these are drivers, won't they need to be compiled as kernel modules? If so, he'll need GCC 3.4....[/QUOTE]

What?  er... Its for the CD/DVD tray media to work on my Epson R300 printer.  Is that good or bad? Gulp!! M

---

### Post by GeneralZod on 2006-01-27
[QUOTE=MJSOnline]My ***!!  What went wrong in the 1st place then?  What a **** ache!! How do I lean stuff like that then?
M[/QUOTE]

To be quite honest, something is *still* very wrong - this is just a workaround.  I have absolutely, 100%, *zero* idea why the original methods didn't work - this whole procedure should, by rights, have worked as follows:

- Go here and follow the 3 or so steps.
- Install build-essential via the repositories.

I'm flummoxed as to why this hasn't worked :confused:

Edit:

[QUOTE=MJSOnline]What?  er... Its for the CD/DVD tray media to work on my Epson R300 printer.  Is that good or bad? Gulp!! M[/QUOTE]

Don't panic just yet :) Follow the original recommendations first.

---

### Post by ubuntumaneh on 2006-01-27
In order to compile a package you need a set of tools that lies in this  build-essential package. You had to install it. But your sources.list was with some problem. Then you corrected it. My mistake was that I didn't realize that the cd or dvd was needed. I still think it is not needed, though (BTW, all my installations I got build-essential from cd.). 
From now on, things will tend to be easier. If you get the gist of terminal, you are going to fly, and see how easy it is. The best way to learn is to used it a lot. Takes time. Also, learn how to use man page. For instance:
man apt-get
or
man <any_command>

Now, is this gutenprint package a driver? If it is, you are supposed to go a little hard core, and compile the kernel. Otherwise, the plain installatino with make will do.

---

### Post by MJSOnline on 2006-01-27
Hmm Ok.  All I need is a few examples to start with.  I did M$Dos years ago, then Windows in 89, I just lost most of the basic knowalge... dafft eh.. 

Ok.  got a far as the make command...  see below.last few lines of the terminal . er.. should it say that?

[B]
Making all in scripts
make[2]: Entering directory `/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1/scripts'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1/scripts'
make[2]: Entering directory `/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1'make[2]: Nothing to be done for `all-am'.
make[2]: Leaving directory `/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1'
make[1]: Leaving directory `/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1'
matthew@Main:/media/SlaveDrive/DLoads/gutenprint-5.0.0-rc1$
[/B]

Matthew

---

### Post by MJSOnline on 2006-01-27
I mean I looking into make a Ubuntu server for videos / music etc for my basement, once its done.  A home cinima.  Have I got any chance getting that up and running, maintaned if I cant get my head round the basics?  Or is that easy??...

M

---

### Post by GeneralZod on 2006-01-27
[QUOTE=MJSOnline]I mean I looking into make a Ubuntu server for videos / music etc for my basement, once its done.  A home cinima.  Have I got any chance getting that up and running, maintaned if I cant get my head round the basics?  Or is that easy??...

M[/QUOTE]

So far, you've been OK with the basics - it's just that, for reasons that seem to baffle everyone in this thread, nothing that should be working out right *is* working out right! :)

---

### Post by ubuntumaneh on 2006-01-27
For the messages you showed us, it seems it the make command was succesful. I really cannot tell. Go for make install. And see if the thing gutenprint is supposed to do is being done.

I think you are in good track to your goals. You have learn a lot and you have keep your patient with all this weird problem. So I believe you are going to have you server soon.

---

### Post by MJSOnline on 2006-01-27
Ok guys.  Many thanks for your help.  Like all posts, that I do, I print them out or store them on disk for futher ref and learning.  Now [here]("http://www.ubuntuforums.org/showthread.php?t=119268") is the post that tells me what to do once this package has been made and installed.  Does it look ok, run ok?

Thanks again. Matthew

---

### Post by ubuntumaneh on 2006-01-27
You are welcome. It seems to be a good thing this driver. Have fun and good work.

---

### Post by MJSOnline on 2006-01-27
Good.  Many thanks again.  Take care.... Matthew.. I am sure I will more questions as the time goes on.. M

Oh.. Got one..  How do I make Ubuntu detect my scanner, part of the HP 3320 printer I have?  I went to Xsane to scan a document. but it says no device found.. 

Sorry again.  If you want me to repost in other forum, just say. M

---

### Post by ubuntumaneh on 2006-01-27
If it was not done automatically during boot, you have to install it.
I advice you to start a new thread, which a title with all the spec of your scan. This will call attention of people who are more familiar with scanners. im not.
But you gave a good idea. I have an old scanner left a drawer here at home. I will give it a try.

---

### Post by MJSOnline on 2006-01-27
No worrys.  Many thanks again.  Matthew

---

