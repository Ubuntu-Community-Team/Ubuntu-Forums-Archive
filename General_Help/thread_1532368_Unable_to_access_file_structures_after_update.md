---
title: "Unable to access file structures after update"
date: 2010-07-16
forum: General Help
---

### Post by Orson1981 on 2010-07-16
I just ran the update manager and am now unable to access any of my files.  Additionally I can not run the software center or run apt-get from the terminal.  Luckily my web browsers and email client are still working.

I first ran the update a few days ago, but for some reason, about 30 or so packages wouldn't download, so update manager installed all but those ~30 packages.  Afterwards everything seemed fine, except the clock was broken on my desktop, which corrected itself after two reboots.

Since that time the only major change I've made to the system is to rollback my version of gcc to 4.3.0 from 4.4.3.  This was done in hopes that the older version of gcc would read a header file in some software I need to get installed (apparently ubuntu doesn't like locale.h).  However, doing so did help.

Today when I got into work I thought I would see if I couldn't finish the update before trying some different versions of gcc, so I ran the update manager again.  This time it downloaded the remaining ~30 packages and installed them, no problem.  It wasn't until I ran apt-get that I noticed that all the icons on my desktop had disappeared.

If you can, please keep in mind that I only started running Linux about 6 days ago, so my knowledge base is very limited. Thanks for the help.

below is the error I get from running apt-get

```
chris@chris-laptop:~$ sudo apt-get install build-essential
apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by apt-get)
apt-get: /usr/local/lib/libstdc++.so.6: version `GLIBCXX_3.4.11' not found (required by /usr/lib/libapt-pkg-libc6.10-6.so.4.8)
```

---

### Post by nothingspecial on 2010-07-16
I`m only guessing here but it could be that you have removed a dependency of apt some how whilst rolling back g++

If I do apt-cache showpkg on apt and  g++  there are all sorts of libc6 libraries and whatever in both dependency lists, nothing exactly the same but I`m thinking that a dependency of a dependency of both apt and g++ have a common dependency, if you see what I mean.

Short of compiling everything from source, which you probably can`t do because of this missing library, I`m stuck.

You may be able to chroot from a live cd and fix it like that but I don`t think so.

Of course I may be talking utter nonsense, and in that case you will just have to wait until someone who Knows what they are talking about comes along...... like I said I`m only guessing.

How did you "roll back" g++?

---

### Post by Orson1981 on 2010-07-16
Thanks for the reply,

I rolled back GCC by going to the website [http://gcc.gnu.org/](http://gcc.gnu.org/) and downloading GCC 4.3.0 from one of the mirrors linked to the site, then followed the instructions to setup, build, configure, and install that version.  I did that last night, and everything was running fine then, and this morning.  It wasn't until I finished the update that everything fell apart.

I've tried updating GCC back to the newer version, but I no longer have access to some of the prerequisite packages that I need to install.

I've also tried creating a new user to see if it will magically fix itself... It didn't.

Lastly, I don't know for certain, but I thought there use to be a 'usr' and/or 'bin' directory in home.  If there was, it no longer shows up when I use 'ls' in the terminal.  This is what I see.

```
chris@chris-laptop:~$ ls
Desktop    examples.desktop  help   obfile    sour
Documents  gcc-4.3.0         mice   Pictures  Templates
Downloads  gmp-5.0.1         Music  Public    Videos
```

---

### Post by nothingspecial on 2010-07-16
Can you post the output of ```
history
```

back to just before you installed the new (old) g++ please.

---

### Post by Orson1981 on 2010-07-16
everything you see below step 140 is something I've tried since the system crashed.  The mice and mice-like things are related to the project I am working on and are attempts to get the software working.

Between 100 and 115 is my attempt at removing gcc and installing the older version through apt-get.  Which didn't work and temporarily destroyed my display driver.

116 to 129 was configuring and installing gcc 4.3.0


```
   88  gcc -v
   89  cd GCC/
   90  gcc-4.3.0/configure
   91  
   92  cd GCC/
   93  ~/gcc-4.3.0/configure 
   94  sudo get-app install gmp
   95  sudo apt-get install gcc-4.3
   96  sudo apt-get remove gcc
   97  gcc -v
   98  sudo apt-get remove gcc-4.1
   99  which gcc
  100  sudo apt-get remove gcc-4.4
  101  sudo apt-get remove gcc-4.1-base 
  102  sudo apt-get remove gcc-4.4-base 
  103  sudo apt-get remove gcc-4.4-base
  104  sudo apt-get remove gcc-4.4-locales 
  105  sudo apt-get remove gcc-4.4-base 
  106  sudo apt-get install gcc-4.3-locales
  107  sudo apt-get autoremove gcc-4.4-base 
  108  csh
  109  sudo apt-get install gcc-4.3
  110  gcc -v
  111  sudo apt-get install gcc
  112  cd ..
  113  gcc -v
  114  sudo apt-get install gcc-4.3
  115  apt-get autoremove
  116  ~/gcc-4.3.0/configure 
  117  cd gmp-5.0.1/
  118  ./configure
  119  make
  120  make install
  121  ch obfile
  122  cd /obfile
  123  ls
  124  cd obfile/
  125  gcc-4.3.0/configure
  126  ~/gcc-4.3.0/configure
  127  make
  128  make install
  129  sudo make install
  130  cd..
  131  cd ..
  132  csh
  133  cd mice/MICE/mgr
  134  make
  135  gcc -v
  136  make -s distclean
  137  make -s
  138  make
  139  csh
  140  cd ../../
  141  cd ..
  142  csh
  143  sudo apt-get install build-essential
  144  cd usr/local/lib/
  145  cd usr/local/lib
  146  cd usr/local
  147  cd usr
  148  cd mice
  149  cd ..
  150  ls
  151  sudo apt-get install build-essential
  152  cd downloads
  153  mkdir help
  154  cd help
  155  cd ..
  156  rm help
  157  rm -f help
  158  cd Downloads/
  159  ls
  160  cd ..
  161  cd help
  162  cd ..
  163  ls
  164  cd gcc-4.3.0/
  165  ls
  166  cd ..
  167  mkdir sour
  168  cd sour
  169  cd ..
  170  cd Downloads/
  171  ls
  172  gcc-4.3
  173  tar xvf gcc-4.3.0.tar.gz 
  174  ls
  175  tar xvf gcc-4.5.0.tar.gz 
  176  ls
  177  cd ..
  178  cd sour
  179  ~/Downloads/gcc-4.5.0/configure
  180  which gmp
  181  cd ..
  182  which gmp
  183  which gimp
  184  cd usr
  185  ls
  186  sudo useradd -G admin Chris
  187  sudo adduser Tom
  188  sudo adduser
  189  sudo adduser tom
  190  ls
  191  history
```

---

### Post by Orson1981 on 2010-07-16
Is it at all possible something was removed from my path? or perhaps moved so that the path no longer points to it?

```
chris@chris-laptop:~$ echo $PATH
/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games

```

---

### Post by nothingspecial on 2010-07-16
I`m still guessing here.

Well first, your path is fine I know that.

I take it you got errors when trying to remove g++ through apt-get, the ones about unmet dependencies? And in that case didn`t actually remove the g++ you had.

So I`m thinking, that building the g++ you downloaded has overwritten something that apt is expecting to be there. You should never build a package without removing the version you already have.

As to what I would do next. If I had the time and was in the mood I might try to fix it somehow. If I just wanted a computer that works, I would make a seperate partition for /home and reinstall (making a /home partition means that all your settings will be there on a new installation.) I also back up /etc/apt/sources.list and any other config files I have modified in /etc such as fstab, modules, etc etc.

Then run ```
dpkg --get-selections | grep install > installed_stuff.txt
``` which gives me a list of packages I have installed.

It is against forum policy to recommend installing but ........ that will take 20 - 30 minutes, where as fixing this could take days.

Or the third choice is to wait and see if someone comes along and says "easy just type blah -vdt "$/'b\regex^\" /usr/bin and that will sort it" which I doubt.

You could try```
 sudo apt-get install -f
``` which is how to fix broken packages, but since it is apt that is broken that will probably fail.

You could download the apt .deb from packages ubuntu.com and try running dpkg on it

Or you could try building apt itself

[http://algebraicthunk.net/~dburrows/blog/entry/howto-get-the-apt-source-repository/](http://algebraicthunk.net/~dburrows/blog/entry/howto-get-the-apt-source-repository/)

I know what I would do.

---

### Post by Orson1981 on 2010-07-16
Thank you for your help.  The only nice thing about just learning a new system is everything that took you a week to learn and implement the first time will only take you a day the second time.

I'll leave this open over the weekend just in case anyone comes by with some bright idea.  After that though, I'll probably just sit down and reinstall everything.  I really need a working machine more than a perfect machine for next week.

---

