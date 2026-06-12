---
title: "E: Couldn't find package libstdc++5"
date: 2010-06-11
forum: General Help
---

### Post by abcuser on 2010-06-11
Hi,
I am trying to install some software that requires libstdcc+5 package.

On Ubuntu 9.10 I did the following:
```
sudo apt-get install libstdc++5
```
and then install software.

But on Ubuntu 10.04 executing the same command I get error:
=======
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libstdc++5
=======

As I see this is C++ library and on Ubuntu 10.04 there is installed version libstdc++6.so file by default, but I need older version of this file (libstdc++5.so).

How to install libstdc++5 on Ubuntu 10.04?
Regards

---

### Post by stoneage on 2010-06-11
You could try installing from the Karmic repository. I don't know if there would be a conflict or dependency problem. 
 
Have a look at [http://packages.ubuntu.com](http://packages.ubuntu.com) for more information and to download.

What are you installing?

---

### Post by anglican on 2010-06-11
> **abcuser said:**
> Hi,
I am trying to install some software that requires libstdcc+5 package.

On Ubuntu 9.10 I did the following:
```
sudo apt-get install libstdc++5
```and then install software.

But on Ubuntu 10.04 executing the same command I get error:
=======
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package libstdc++5
=======

As I see this is C++ library and on Ubuntu 10.04 there is installed version libstdc++6.so file by default, but I need older version of this file (libstdc++5.so).

How to install libstdc++5 on Ubuntu 10.04?
Regards
libstdc++5 actually last appeared in the jaunty repositories. You can get it from:

[http://packages.ubuntu.com/en/jaunty/libstdc++5](http://packages.ubuntu.com/en/jaunty/libstdc++5)

It installs fine into karmic and lucid. There's quite a bit of ageing software, such as drivers for old printers, that were compiled against libstdc++5 and need this package which will disappear when jaunty does - which is not too far away now!

H

---

### Post by stoneage on 2010-06-11
So that's where I got it from? 

I assumed it was available for Karmic because I have it installed, thanks for the correction :)

---

### Post by abcuser on 2010-06-11
anglican, thanks I have downloaded/installed the file from your link and now product installed successfully.

---

