---
title: "Problems installing new kmymoney2-0.8.3"
date: 2006-03-25
forum: General Help
---

### Post by sjoseph on 2006-03-25
I am following the directions to install kmymoney on ubuntu and i get this error message when i run config in terminal. any thoughts. i had an older vs. of kmymoney and it installed fine from the repository, but the new vs. was from sourceforge. here is the result of the config.

sjoseph@ubuntu:~/kmymoney/kmymoney2-0.8.3$ ./configure
checking build system type... i686-pc-linux-gnuoldld
checking host system type... i686-pc-linux-gnuoldld
checking target system type... i686-pc-linux-gnuoldld
checking for a BSD-compatible install... /usr/bin/install -c
checking for -p flag to install... yes
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for kde-config... /usr/bin/kde-config
checking where to install... /usr (as returned by kde-config)
checking for style of include used by make... GNU
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH

---

### Post by sjoseph on 2006-03-26
any thoughts would be appreciated..

---

### Post by halitech on 2006-03-26
by the looks of the output, it looks like it is failing because there is no C compiler. try going into Synaptic and adding gcc. I had something doing the same thing and once I installed gcc it worked fine.

hth

---

### Post by Ramses de Norre on 2006-03-26
sudo apt-get install build-essential (includes gcc and many other compilling-related programs).

EDIT: it was build indeed ;)

---

### Post by Hairy_Palms on 2006-03-26
i think u mean 
sudo apt-get install buil**d**-essential

---

### Post by halitech on 2006-03-26
Thanks Ramses, I really need to write that command down so I can recommend it for others

---

### Post by sjoseph on 2006-03-26
thanks all, i'll give it a try..

---

### Post by sjoseph on 2006-03-26
so now it seems to compile but then it is looking for libjpeg. i tried the make command and it didn't accept it. i tried the make install command and it wouldn't accept it. i tried a sudo apt-get install libjpeg and it didn't find it. (i don't like giving up)

---

### Post by Ramses de Norre on 2006-03-26
sudo apt-get install libjpeg62 libjpeg62-dev
As I said, make wont work untill ./configure says that everything is ok. 
And to search for a package name: apt-cach search keyword.

---

### Post by sjoseph on 2006-03-26
here's the latest, it compiled more, the libjpeg helped, but

checking for libz... -lz
checking for libpng... -lpng -lz -lm
checking for libjpeg6b... no
checking for libjpeg... -ljpeg
checking for perl... /usr/bin/perl
checking for Qt... configure: error: Qt (>= Qt 3.0 and < 4.0) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

i tried to download libjpeg6b, but apt-get couldn't find it..

---

### Post by Ramses de Norre on 2006-03-26
> checking for Qt... configure: error: Qt (>= Qt 3.0 and < 4.0) (headers and libraries) not found. Please check your installation!
You'll need kde libraries.

Run this all in the source dir, it will be done automaticaly then.
```
sudo -s
apt-get install auto-apt
auto-apt update
auto-apt updatedb
auto-apt update-local
auto-apt run ./configure
./configure
make
apt-get install checkinstall
checkinstall -D make install

```

---

### Post by sjoseph on 2006-03-26
sorry to keep bothering you, i'm pretty new at this. what is the source directory. is that the one where the file i want installed is located.

---

### Post by Ramses de Norre on 2006-03-26
The directory you untarred the source into. (I always make a hidden directory for each program I install from source in my homedir, to do so make a dir in your home folder and start the name with a dot.)

---

### Post by GeneralZod on 2006-03-26
Since an earlier version of kmymoney is in the repos, a simple:

```

sudo apt-get build-dep kmymoney2

```

should sort out most of the dependencies for you.

---

