---
title: "64  bit and guitar pro 6"
date: 2011-05-12
forum: General Help
---

### Post by wicki on 2011-05-12
HI ...New to Ubuntu running the latest 11.04 and i am really enjoying the software it does all i want except run Guitar pro 6.

 I have downloaded the Linux version which is supposed to run but when I try to install it I get a message telling me its the wrong version and something about "i386" I did some research which suggested loading 32 bit libs this i have done but it still wont install any one got any suggestions how to get it to work ?

Thanks !:guitar:

---

### Post by perdan on 2011-05-12
This thread seems to have som useful suggestions:
[http://ubuntuforums.org/showthread.php?t=1458626](http://ubuntuforums.org/showthread.php?t=1458626)

---

### Post by bloozguy on 2011-05-23
I am on Ubuntu 11.04 (64 bit).

 GuitarPro6 USED to work but I downloaded revisions and now it gets a segfault.
I tried downloading the latest version of GuitarPro6 (GuitarPro6Demo-rev9626.deb)
and went through the getlib kabuki : [http://ubuntuforums.org/showthread.php?t=1458626](http://ubuntuforums.org/showthread.php?t=1458626) and  still no dice:mad:

---

### Post by wicki on 2011-05-23
Given up gone back to 32 bit ..everything is good.

---

### Post by bloozguy on 2011-05-26
When you load the 32 bit version you are warned that it is a "bad quality" package and this may cause you problems.
 Seems GuitarPro6 is just not ready for Linux  ... back to the somewhat clunky Tux Guitar.:mad:

---

### Post by bloozguy on 2011-05-26
Okay one reason it's not working is that it is going after libraries in /lib instead of /lib32. How can you make it or fool it into doing the "right" thing without messing up your 64 bit apps?:confused:

---

### Post by bloozguy on 2011-06-22
Finally got it to work after I got ahold of the GP people.

The solution is to dumb down the 32 bit libraries for any version of Ubuntu newer than Maverick.

"It seems a bug in the latest ia32-libs causes some trouble to applications that uses 32bit libraries (GP6 use 32 bit libraries too).

A workaround exists, simply downgrade the ia32-libs package.

Follow these guidelines to downgrade ia32:
- download the package from this page [http://packages.ubuntu.com/maverick/amd64/ia32-libs/download](http://packages.ubuntu.com/maverick/amd64/ia32-libs/download)
- run a terminal and go to the directory where the .deb is stored
- execute this command line: sudo dpkg --force-downgrade -i ia32-libs_20090808ubuntu9.1_amd64.deb "

:)

---

### Post by Dangertux on 2011-06-22
You might also be interested in checking out the Tux Guitar project. It is compatible with guitar pro

Edit I need to learn to read it was already mentioned. Oh well I still think it's a great bit of software.

---

