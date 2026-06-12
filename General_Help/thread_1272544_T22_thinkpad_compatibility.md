---
title: "T22 thinkpad compatibility"
date: 2009-09-22
forum: General Help
---

### Post by kyle6513 on 2009-09-22
hi everyone =]
thanks in advance for anyone who takes the time to read or post here,
first of all I'm running xubuntu 9.04 on an IBM T22 laptop and I found this article,
[http://ubuntuthinkpad.blogspot.com/](http://ubuntuthinkpad.blogspot.com/)
now I can see that its VERY out dated,
things I would like to get working would be,
-speedstep
-Ir-DA
-scroll button
-3d acceleration - SAVAGE IX (as minimal as it would be, would still help running this super slow                 system T.T
and yeah thats pretty much it,
I've found an article on how to get Ir-DA working, not T22 specific but for laptops,
[http://tuxmobil.org/Infrared-HOWTO/infrared-howto-c-getting-started.html](http://tuxmobil.org/Infrared-HOWTO/infrared-howto-c-getting-started.html)
I've started on that but I can't make the irda-utils part,
the dependicies are,
[00-dirtree]("http://www.t2-project.org/packages/00-dirtree.html") [autoconf]("http://www.t2-project.org/packages/autoconf.html") [automake]("http://www.t2-project.org/packages/automake.html") [bash]("http://www.t2-project.org/packages/bash.html") [binutils]("http://www.t2-project.org/packages/binutils.html") [bzip2]("http://www.t2-project.org/packages/bzip2.html") [coreutils]("http://www.t2-project.org/packages/coreutils.html") [diffutils]("http://www.t2-project.org/packages/diffutils.html") [gawk]("http://www.t2-project.org/packages/gawk.html") [gcc]("http://www.t2-project.org/packages/gcc.html") [glibc]("http://www.t2-project.org/packages/glibc.html") [grep]("http://www.t2-project.org/packages/grep.html") [gzip]("http://www.t2-project.org/packages/gzip.html") [libtool]("http://www.t2-project.org/packages/libtool.html") [linux-header]("http://www.t2-project.org/packages/linux-header.html") [m4]("http://www.t2-project.org/packages/m4.html") [make]("http://www.t2-project.org/packages/make.html") [mktemp]("http://www.t2-project.org/packages/mktemp.html") [net-tools]("http://www.t2-project.org/packages/net-tools.html") [perl]("http://www.t2-project.org/packages/perl.html") [sed]("http://www.t2-project.org/packages/sed.html") [sysfiles]("http://www.t2-project.org/packages/sysfiles.html") [sysstat]("http://www.t2-project.org/packages/sysstat.html") [tar]("http://www.t2-project.org/packages/tar.html") [util-linux]("http://www.t2-project.org/packages/util-linux.html")

```
kyle@kyle-laptop:~$ sudo apt-get install 00-dirtree autoconf automake bash binutils bzip2 coreutils diffutils gawk gcc glibc grep gzip libtool linux-header m4 make mktemp net-tools perl sed sysfiles sysstat tar util-linux
[sudo] password for kyle: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 00-dirtree
```

so I removed 00-dirtree, (someone find where that is?)
anyways, running each through the command line the following happened
```

E: Couldn't find package 00-dirtree
autoconf is already the newest version.
automake is already the newest version.
automake set to manually installed.
bash is already the newest version.
binutils is already the newest version.
bzip2 is already the newest version.
coreutils is already the newest version.
E: Couldn't find package diffutils
gawk is already the newest version.
gcc is already the newest version.
E: Couldn't find package glibc
grep is already the newest version.
gzip is already the newest version.
libtool is already the newest version.
E: Couldn't find package linux-header
m4 is already the newest version.
make is already the newest version.
mktemp is already the newest version.
net-tools is already the newest version.
perl is already the newest version.
sed is already the newest version.
E: Couldn't find package sysfiles
sysstat is already the newest version.
tar is already the newest version.
util-linux is already the newest version.
```

now I believe I need the ones that couldn't be found,

(as per [http://www.t2-project.org/packages/irda-utils.html](http://www.t2-project.org/packages/irda-utils.html))
I have run these through sudo apt-get install,


I just want someone who's smart enough about this to go through it and make sure that these guides will work or if they are not even needed (scroll button definitely doesn't work)

thanks in advance,
kyle
:)

---

### Post by x22 on 2009-09-24
> t22 scroll button

on my t22, I have a red trackpoint on the keyboard, and
three clickers on the palmrest: 2 red, and one (middle)
blue.  

the trackpoint moves the cursor; the left clicker is
left click, the right clicker is right click, the middle
clicker is "cut and paste"

scroll button?

---

### Post by kyle6513 on 2009-10-23
> **x22 said:**
> > t22 scroll button

on my t22, I have a red trackpoint on the keyboard, and
three clickers on the palmrest: 2 red, and one (middle)
blue.  

the trackpoint moves the cursor; the left clicker is
left click, the right clicker is right click, the middle
clicker is "cut and paste"

scroll button?

on windows xp say you're in firefox and you middle click somewhere that isnt a link, you can scroll down and the speed is determined by the distance between the inital click and where the mouse is at the moment.

---

### Post by fluffman86 on 2009-10-23
By default, the middle button will paste your currently selected text, separate from copy/paste.  

[http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T400#Scrolling_with_Trackpoint](http://www.thinkwiki.org/wiki/Install_Ubuntu_9.04_%28Jaunty_Jackalope%29_on_a_ThinkPad_T400#Scrolling_with_Trackpoint)

^ That's what I used on my Thinkpad to enable scrolling with the nub while holding the middle button, without disabling the paste functionality above.  At least, it worked in 8.10 a year ago before I sold my Thinkpad.

---

