---
title: "64 vs 32 bit problem with a compiler"
date: 2011-07-15
forum: General Help
---

### Post by hipogrito on 2011-07-15
Hi,

Long time Ubuntu user... in 32 bit machines.

Got a new laptop: 64 bit Dell with an i5 processor and an unbelievable pink flamingo colour... I wonder why it was discounted... :D

So, I download Ubuntu 11.04 (I am using 10.4 in another laptop, 32 bits)... everything fine. I got nearly everything working.

The biggest problem: For work I need gnush C compilers for Renesas processors. They give you 32 bits rpms. We alien them into deb. They work perfectly in Ubuntu 32 bits. But, when I try to install the package in the 64 bit system, it fails. Basically it cannot link some libraries:

```

sudo dpkg --force-architecture --install gnush_v0901_elf.deb 
[sudo] password for hipo: 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
(Reading database ... 179582 files and directories currently installed.)
Preparing to replace gnush-v0901-elf:i386 1-2 (using gnush_v0901_elf.deb) ...
Unpacking replacement gnush-v0901-elf:i386 ...
dpkg: dependency problems prevent configuration of gnush-v0901-elf:i386:
 gnush-v0901-elf:i386 depends on libc6 (>= 2.3).
 gnush-v0901-elf:i386 depends on libncurses5 (>= 5.6+20071006-3).
 gnush-v0901-elf:i386 depends on zlib1g (>= 1:1.1.4).
dpkg: error processing gnush-v0901-elf:i386 (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnush-v0901-elf:i386


```

I have gone and install libc6-i386 and I have tried multiple easy things and no luck. We know that there is an obscure way of doing it, editing some bits here and there... hacking basically, but I  try not to go to the dark side and I wonder if there is an easier way... a better way... a cleaner way... THE WAY! ... or maybe not...


So, question for people with experience in things like this?

What should I do?

A. Install the 32 bit Ubuntu and forget about all this.

B. Something magic to link the 386 libraries? That great solution that somebody has tried and worked?

C. Install Fedora 15 (my computer at work uses Fedora 15 64 bits and I do not have these problems with the packages... I've got others though, but easier to solve)... But I am a long time Ubuntu fan... although scratching my head with the new Unity thingy... new user interfaces, in my opinion and in general, should reduce the number of clicks to do stuff, not increase them... at least for the people like me that work all day in machines like this... anyway...

Thanks for your suggestions beforehand!

Regards,
Hipo

---

### Post by idoitprone on 2011-07-15
> **hipogrito said:**
> Hi,



Got a new laptop: 64 bit Dell with an i5 processor and an unbelievable pink flamingo colour... I wonder why it was discounted... :D


Are you a girl? Not everyone like looking at flamboyant colors on their laptops everyday.
[https://help.ubuntu.com/community/32bit_and_64bit](https://help.ubuntu.com/community/32bit_and_64bit)


i hope i get the name of the package right
```
sudo apt-get install ia32-libs
```You are missing the 32 bit binaries such as the important libc

You may have to install other packages to meet those dependencies

or method 2 
[http://ubuntuforums.org/showthread.php?t=474790](http://ubuntuforums.org/showthread.php?t=474790)

---

### Post by hipogrito on 2011-07-15
Hi,

A guy... a cheap guy... that's why I am making fun of myself... If I save 150 bucks... give me a pink flamingo one! ;)

Now back to the thing, I already installed that package.

```

sudo apt-get install ia32-libs
[sudo] password for hipo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
ia32-libs is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```


maybe I am missing some environment variable so that the package looks in there?

Thanks!

Regards,
Hipo

---

### Post by idoitprone on 2011-07-15
i am poofed. Last time i  remember it working long long ago since i got lucky and did not miss any dependencies

```
 gnush-v0901-elf:i386 depends on zlib1g (>= 1:1.1.4).
```that dependency might be a problem since it not in the default i32-libs
you have to search it yourself

[http://packages.debian.org/squeeze/ia32-libs](http://packages.debian.org/squeeze/ia32-libs)

---

### Post by hipogrito on 2011-07-15
Hi,

Ooooooops, I guess this is going to get messy... I'll prepare the mud pants...

Thanks for the suggestion though.

```

sudo dpkg --force-all --install zlib1g_1.2.3.4.dfsg-3_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package zlib1g:i386.
dpkg: error processing zlib1g_1.2.3.4.dfsg-3_i386.deb (--install):
 zlib1g:i386 1:1.2.3.4.dfsg-3 (Multi-Arch: no) is not co-installable with zlib1g:amd64 1:1.2.3.4.dfsg-3ubuntu3 (Multi-Arch: same) which is currently installed
Errors were encountered while processing:
 zlib1g_1.2.3.4.dfsg-3_i386.deb

```

Regards,
Hipo

---

### Post by idoitprone on 2011-07-15
> **hipogrito said:**
> Hi,

Ooooooops, I guess this is going to get messy... I'll prepare the mud pants...

Thanks for the suggestion though.

```

sudo dpkg --force-all --install zlib1g_1.2.3.4.dfsg-3_i386.deb 
dpkg: warning: overriding problem because --force enabled:
 package architecture (i386) does not match system (amd64)
Selecting previously deselected package zlib1g:i386.
dpkg: error processing zlib1g_1.2.3.4.dfsg-3_i386.deb (--install):
 zlib1g:i386 1:1.2.3.4.dfsg-3 (Multi-Arch: no) is not co-installable with zlib1g:amd64 1:1.2.3.4.dfsg-3ubuntu3 (Multi-Arch: same) which is currently installed
Errors were encountered while processing:
 zlib1g_1.2.3.4.dfsg-3_i386.deb

```Regards,
Hipo

[https://help.ubuntu.com/community/DebootstrapChroot](https://help.ubuntu.com/community/DebootstrapChroot)
you can always try a 32 bit chroot.
I just posting suggestions.
btw, i am lazy. i cannot help you with the chroot since i kidda hate setting stuff to get things workin.
I look at those command and like nah screw this app lol
I guess wait until someone that is smarter than me to enter the thread
^ i win at making fun at myself
I do it at every post possible

---

### Post by hipogrito on 2011-07-16
Hi,

No luck installing the compilers... sooooo, I installed Ubuntu 11-4 32 bits and everything just works... yeah, not all the memory is used but the machine just works fine.

Thanks!


And now a free rant from a quite happy Ubuntu user for the past 5 years... but with a smile :)


[rant]
One thing I think Linux/developers have to put their act together yet is the rpm vs deb vs 32 vs 64... like in my case, the company providing the compilers only offers 32 bit rpms. And even if alien converts to deb, I get a "OMG! DO NOT INSTALL THIS PACKAGE!!!!" type of message when installing it in Ubuntu 11.4. It just works though. But if you try to go to 64 bits, which all the new computers are... for several years... then your problems grow exponentially...

And the second thing, and this is for Ubuntu, that needs to be solved is... please, put the freaking Sun Java JRE in the main release... c'mon... you know we need it... you know we have to go to Ubuntuforums each time we want to install it, read the instructions and use the command line to isntall it... you know we geeks can do it... but... c'mon... it does not hurt to have it there or to have a non command line way to install it... Linux is still an OS that I cannot install in my father computer... I cannot tell him, go to the command line and bla bla bla... but it is sooooo close.... but it's been sooooo close for soooo long....

[\rant]


Now, back to scratching my head with Unity...

Thanks!

And be happy!

And do not waste much time installing things in your computers... it is Summer in the North hemisphere... go and have a nice time outdoors.

Poor suckers if you are in the South now... just build a snowman... 

Regards,
Fran

---

