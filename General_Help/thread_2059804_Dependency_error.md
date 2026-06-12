---
title: "Dependency error"
date: 2012-09-18
forum: General Help
---

### Post by layers on 2012-09-18
I need to install Codeblocks, the Arduino version, and I am following this guide [http://www.arduinodev.com/guide-to-arduino-development-environment-codeblocks/](http://www.arduinodev.com/guide-to-arduino-development-environment-codeblocks/)  and I get stuck in the very beginning. Why does it not like me?

> ibo@ibo-vaio:~$ sudo apt-get install codeblocks g++ gcc-avr avr-libc avrdude cutecom
[sudo] password for ibo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
g++ is already the newest version.
g++ set to manually installed.
gcc-avr is already the newest version.
avr-libc is already the newest version.
avrdude is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  cutecom: Depends: libqt4-qt3support (>= 4.5.1) but it is not going to be installed
E: Broken packages
ibo@ibo-vaio:~$

So, is it telling me to install  libqt4-qt3support? When I try doing that in synaptic it gives error again.

---

### Post by jrog on 2012-09-18
> **layers said:**
> I need to install Codeblocks, the Arduino version, and I am following this guide [http://www.arduinodev.com/guide-to-arduino-development-environment-codeblocks/](http://www.arduinodev.com/guide-to-arduino-development-environment-codeblocks/)  and I get stuck in the very beginning. Why does it not like me?



So, is it telling me to install  libqt4-qt3support? When I try doing that in synaptic it gives error again.
Does 

```
sudo apt-get install -f
```

fix the issue?

---

### Post by jerrrys on 2012-09-18
4.5.1 or better is not in the repositories.

[http://packages.ubuntu.com/precise/libqt4-qt3support](http://packages.ubuntu.com/precise/libqt4-qt3support)

[http://www.google.com/search?q=libqt4-qt3support+4.5.1&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=libqt4-qt3support+4.5.1&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)

---

### Post by layers on 2012-09-18
install -f does nothing


> **jerrrys said:**
> 4.5.1 or better is not in the repositories.

[http://packages.ubuntu.com/precise/libqt4-qt3support](http://packages.ubuntu.com/precise/libqt4-qt3support)

[http://www.google.com/search?q=libqt4-qt3support+4.5.1&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a](http://www.google.com/search?q=libqt4-qt3support+4.5.1&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a)
Soo, I need to update it from somewhere else? Or it just won't work?

But the first link says 4.6.2 is in lucid updates, so it is in the repos? [http://packages.ubuntu.com/lucid/libqt4-qt3support](http://packages.ubuntu.com/lucid/libqt4-qt3support)

---

### Post by jerrrys on 2012-09-18
My mistake :oops: you are correct.

what happens if you:

sudo apt-get install libqt4-qt3support

also a force install may be possible

---

### Post by layers on 2012-09-18
> ibo@ibo-vaio:~$ sudo apt-get install libqt4-qt3support
[sudo] password for ibo: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help resolve the situation:

The following packages have unmet dependencies:
  libqt4-qt3support: Depends: libqt4-designer (= 4:4.6.2-0ubuntu5) but it is not going to be installed
                     Depends: libqt4-network (= 4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu5.4 is to be installed
                     Depends: libqt4-sql (= 4:4.6.2-0ubuntu5) but it is not going to be installed
                     Depends: libqt4-xml (= 4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu5.4 is to be installed
                     Depends: libqtcore4 (= 4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu5.4 is to be installed
                     Depends: libqtgui4 (= 4:4.6.2-0ubuntu5) but 4:4.6.2-0ubuntu5.4 is to be installed
E: Broken packages
ibo@ibo-vaio:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 20 not upgraded.
ibo@ibo-vaio:~$ .

---

### Post by jrog on 2012-09-18
> **layers said:**
> .
If you try:

```
sudo dpkg --configure -a
```

and then:

```
sudo apt-get install -f
```

are the results still the same? If so, you might try removing any unnecessary programs, clearing out APT's cache, updating your repo data, and then running those commands again, as in:

```
sudo apt-get autoremove
sudo apt-get autoclean
sudo apt-get clean
sudo apt-get update
sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get dist-upgrade
```

---

### Post by layers on 2012-09-18
ran every command (but the last one, 10.04 for me), still same thing

---

### Post by layers on 2012-09-18
Solved: don't know why.

I searched for anything with "libqt" in software center, and removed it. Then it installed.[-(


thanks for the help

---

### Post by jrog on 2012-09-18
> **layers said:**
> Solved: don't know why.

I searched for anything with "libqt" in software center, and removed it. Then it installed.[-(


thanks for the help
Strange. I'm with you on the "don't know why" part. Glad it worked out, though.

EDIT: Actually, see my next post.

---

### Post by jrog on 2012-09-18
> **layers said:**
> ran every command (but the last one, 10.04 for me), still same thing
Oh! Well, actually, I think *this* may be the source of your problem, if you're avoiding dist-upgrade (the last of the commands I told you to use) because you think it will upgrade you to a different release of Ubuntu. It won't, and you should typically use dist-upgrade in preference to upgrade. Here's why: upgrade by itself will not install new packages under any circumstances if some version of them is not already on your system, and it will not remove old packages, either -- so, in a case where a package has a new dependency that you don't already have in some version, or where some other package needs to be removed because of some conflict, apt-get upgrade won't do it. Dist-upgrade will. From the man page for apt-get:

> upgrade
           upgrade is used to install the newest versions of all packages currently installed on the system from the sources enumerated in /etc/apt/sources.list. Packages currently installed with new versions available are retrieved and upgraded; **under no circumstances are currently installed packages removed, or packages not already installed retrieved and installed. New versions of currently installed packages that cannot be upgraded without changing the install status of another package will be left at their current version.** . . . 

       dist-upgrade
           **dist-upgrade in addition to performing the function of upgrade, also intelligently handles changing dependencies with new versions of packages . . . and it will attempt to upgrade the most important packages at the expense of less important ones if necessary. The dist-upgrade command may therefore remove some packages.**

It could be that avoiding dist-upgrade managed to get some dependencies mixed up somewhere on your system, because upgrade wasn't removing and/or installing things that really needed to be removed/installed. (You can convince yourself that dist-upgrade won't change your Ubuntu to a new release by noting that dist-upgrade uses the sources listed in your /etc/apt/sources.list file, which should point only to the release that you wish to continue using; it couldn't possibly pull packages from other releases, in that case.)

---

