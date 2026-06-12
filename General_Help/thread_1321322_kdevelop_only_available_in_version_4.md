---
title: "kdevelop only available in version 4 ?"
date: 2009-11-09
forum: General Help
---

### Post by SpaceTeddy on 2009-11-09
Hi Ubuntu folks, 

as i do not know where to put this, i hope someone will shed some light on this topic for me.

Currently, only Kdevelop4 is distributed with Ubuntu (yes, Ubuntu - the gnome one. I have been running kdev in Ubuntu for over a year without a problem). 

My question is, why does a stable version of Ubuntu (9.10) ONLY deploy a BETA version of a software (as of Nov 4, kdev is in beta6). Deployed in 9.10 is beta5, from august '09 (73 known bugs which are fixed to beta6, and probably more to be found)

The reason why i am bringing this up is that kdev is (currently) breaking any development which has been previously been done with kdev 3.5. Since this is not offered anymore, anybody wishing to develop with 9.10. Firstly, there is no automake to cmake conversion, and the automake module for kdev has not been compiled in (because it is beta - go figure). So the cmake files have to be written manually - for a bigger project (like mine) this is a total pain (but i have done it - and they kind of work by now - after a day of reading cmake manuals - and no, the scripts supplied on the cmake page DO NOT work correctly). Secondly, the bugs still in the current version are pretty heavy (example: when pressing F9 for debuging, it does not work. In addition, F9 is also assigned to another random function, rendering it ambiguous for the next time until it is manually deleted from the shortcuts - this is REALLY annoying)

So, why does a beta version get distributed in a stable version of ubuntu without the option of using the "old" or "stable" one or in other words - why is there no kdevelop3.5 package ?

PS: i bet nobody answers this :)

---

### Post by hickmott on 2009-11-10
I'm running into pretty severe problems with KDevelop 4, too.

Have you found any documentation for it? Everything I've seen on the KDevelop site is for version 3. I haven't even figured out how to get the execute button to light up for the sample Hello World program it generates as a C++ default new application.

KDevelop is my main application. I may have to roll back to Ubuntu 9.04 on this one.

---

### Post by SpaceTeddy on 2009-11-10
i've tried to only roll back kdevelop. As gnome does not depend on the KDE libs, i can just install the "old" versions of the packages. However, this is a huge task (after manually installing about 30 packages i gave up, since the old version of kdevelop started but the menus were all screwed up. I could not fix this at all... so i have to agree that the only option is a roll-back to 9.04 or 8.04. 

I would be very interested in someone explaining why the choice was done to only include kdevelop4 without any legacy support...

---

### Post by 10101011 on 2009-11-13
I'm having similar problems with KDevelop4.

I've spent some time trying to get a several hundred file CMake project ported into a new kdevel4 project, since the kdevel3 project files don't seem to work. And I still can't get it right - I don't know where to pick the build type, configure doesn't work and has to be done manually, etc.

I've also been looking around online to try to find out how to rollback to KDevelop3 - I'm pretty sure that we're not the only developers who use Ubuntu and KDevelop - but I can't seem to find a thing ([except for this]("http://apaku.wordpress.com/category/kde/kdevelop/")).

If you guys find a solution, please come back here and give us an update, and I'll do the same.

Thanks.

---

### Post by hickmott on 2009-11-13
I suspect rolling back to version 3 is difficult. It requires QT and KDE < 4.0. This may be why Ubuntu shipped with a beta version of KDevelop; to keep supporting KDevelop 3, they'd also have had to continue supporting back versions of QT and KDE in parallel with the current versions. That's a lot of effort.

10101011, The post you reference suggests building the latest KDevelop 4 beta from source. I'm trying this now. If that doesn't work, it's back to 9.04.

---

### Post by 10101011 on 2009-11-13
Yep, rolling back turned out to be difficult.

kdelibs4-dev is still in Karmic (which is the version for KDE3, oddly enough).

After removing kdelibs5-dev to install kdelibs4-dev, installing qt3-apps-dev and libdb4.7-dev, I configured with the following command:

./configure --without-arts --disable-ada --disable-bash --disable-fortran --disable-haskell --disable-java --disable-pascal --disable-perl --disable-php --disable-python --disable-ruby --disable-sql --disable-antproject --disable-scriptproject --disable-trollproject --disable-clearcase --disable-perforce --disable-subversion

I had to add --without-arts since I found no (easy) way of getting mcopidl.

Then, after having compile errors with the antlr module, I tried "make -k", which ignores most errors.

To make a long story short, I still can't get it compiling.

Edit: I'm talking about compiling KDevelop 3.5 here

---

### Post by hickmott on 2009-11-13
The beta6 version does seem to be a bit more stable. I also found it helpful to do

rm -rf ~/.kde/share/apps/kdev*

Before that, nothing I tried would get it to actually run a program. Afterwards I had no trouble getting the sample app to run under the debugger. So, it'll edit, compile, and debug the sample app. It's a start. Now to try it on some real code.

---

### Post by andrewl_oz on 2009-11-15
The compile is still in progress, but switching to gcc/g++ version 4.2 appears to be working well so far - time will tell!  Just install gcc and g++ 4.2, and set the links for gcc,g++,cpp and gcov to *-4.2, clean the failed build and restart. Make -j4 improves the build speed but will result in an occasional error requiring a restart - programmatic dependencies are not handled.  - Andy

---

### Post by andrewl_oz on 2009-11-15
That's it: kdevelop 3.5.5 compiles are runs using gcc version 4.2.  No serious work done with it yet, but at least it loads an existing project without issue.  The config I used was:

./configure --disable-ada --disable-java --disable-pascal --disable-antproject --disable-clearcase --disable-perforce  --disable-csharp  --without-arts

but I'm sure other combinations would work.

One day I'm sure kdevelop 4 will be up to scratch, but it may be a while.  In the interim it would be good if the 3.5 strand could be made an option from the main ubuntu repository.

- Andy

---

### Post by andrewl_oz on 2009-11-15
Remember to switch your compiler back to version 4.4!  The attached script does a basic job of switching versions if you like to use it.

- Andy

---

### Post by hickmott on 2009-11-16
Thank you. That works well.

It looks like KDevelop4 is supposed to be released non-beta in February. I'll probably try it again in Ubuntu 10.04.

---

### Post by sylvaticus on 2009-11-18
Hello andrewl_oz, could you please post a more detailed how-to on how to get kdevelop 3.5 running in ubuntu 9.10 (sorry I am little dumb..).. I mean:
- which packages to have installed
- which kdevelop tarbal to get
- configure options
- what's about gcc compiler ???


thank you... I'm sure this would be useful for lots of ubuntu users!!!

---

### Post by sylvaticus on 2009-11-18
I managed getting a working kdevelop 3.5 in ubuntu 9.10 addind this line to sources.list and forcing the version (thorugh synaptic) of kdevelop and kdevelop-data to 3.5.5:

```
deb http://ftp5.gwdg.de/pub/opensuse/repositories/home:/amilcarlucas/xUbuntu_9.04/ ./
```

---

### Post by Rob_Frohne on 2009-11-18
The previous repository didn't seem to have everything in the menus appearing, but I found that another repository that worked just fine.  Note that the files are installed in /opt/kde3/...

Also, I did not install all of KDE3, just kdevelop-kde3 and kdevelop-kde3-doc.

This page led the the repository:
[https://wiki.kubuntu.org/Kubuntu/Kde3/Karmic](https://wiki.kubuntu.org/Kubuntu/Kde3/Karmic)

and the lines to add to your sources.list are:

deb [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) karmic main
deb-src [http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu](http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu) karmic main

It is great to have the kdevelop IDE working as usual again.

Rob 
:D

---

### Post by csq on 2009-11-24
hi, [sylvaticus]("http://ubuntuforums.org/member.php?u=246978"),
After adding this line to the end of the sources.list, what should I do? I go back to check the kdevelop in synaptic package manager, the version is still 4:3.9.95.

thanks
siqi

---

### Post by OzzyLucky on 2009-11-24
Hi csq,

I think you have to update your lists with

sudo apt-get update

then the new packages should appear in synaptic.

I also tried to install kdevelop-kde3 and kdeveop-kde3-doc. The fact is that they come with some dependencies ( kdeveop-data-kde3 and others), and when I applied for installing, I get this error message

E: /var/cache/apt/archives/kdevelop-kde3_4%3a3.5.10-0ubuntu6_amd64.deb: trying to overwrite '/usr/share/man/man1/kdevelop.1.gz', which is also in package kdevelop 4

Seems that I have to uninstal kdevelop4 to avoid that, but if I do that, then kdevelop would not work amymore...

I still don't know what to do with my old .kdevelop files...

Please help...

---

### Post by santana on 2009-11-24
Worked thanks a million!!!! 

this may be the better link: [http://apt.pearsoncomputing.net/install.html](http://apt.pearsoncomputing.net/install.html)


> **OzzyLucky said:**
> 
I get this error message

E: /var/cache/apt/archives/kdevelop-kde3_4%3a3.5.10-0ubuntu6_amd64.deb: trying to overwrite '/usr/share/man/man1/kdevelop.1.gz', which is also in package kdevelop 4


Yeah, I hit that too, but got by it. so from start to finish:



```

# 1. Add these lines to your /etc/apt/sources.list file:
deb http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/kde3-maintainers/ppa/ubuntu karmic main

# 2. Add the GPG signing key:
wget http://apt.pearsoncomputing.net/public.gpg
sudo apt-key add public.gpg 

# 3 Refresh the package list
sudo apt-get update

# 3. Remove kdev 4
sudo apt-install purge kdevelop

# 4. Install kdev 3
sudo apt-get install kdevelop-kde3 kdevelop-kde3-doc

# 5. Launch
/opt/kde3/bin/kdevelop &

```

---

### Post by csq on 2009-11-24
Santana,

should it be

sudo apt-get purge kdevelop

instead of,

sudo apt-install purge kdevelop


 I finally switch back to kdevelop3 :)

Thank you.

---

### Post by al.batros on 2009-12-16
> 
this may be the better link: [http://apt.pearsoncomputing.net/install.html](http://apt.pearsoncomputing.net/install.html)

I can't access any more to the gpg from this website :confused:

---

### Post by agestrada on 2012-02-23
Two years later and they still have a buggy version in Lucid repo. Kdevelop 4.0 can't use standard input when debugging or running, crashes every time you close it and more ...

Building from source the latest version is a pain as you have to get and build each one of the plugins as well, which in my case gave my errors with the very first one. Couldn't find any automated process.

---

