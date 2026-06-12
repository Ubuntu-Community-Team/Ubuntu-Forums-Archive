---
title: "How to install libglew 1.7"
date: 2012-07-03
forum: General Help
---

### Post by einstein**-7 on 2012-07-03
Hey there, I'm using 12.04 and i'm trying to install the libglew version 1.7 i've downloaded the package files but i'm not sure how to build/install  them.
Any help appreciated.

---

### Post by matt_symes on 2012-07-03
Hi

Can you post a link to where you downloaded then from ?

I will take a look and see if i can build them and tell you how i did it.

Kind regards

---

### Post by einstein**-7 on 2012-07-03
> **matt_symes said:**
> Hi

Can you post a link to where you downloaded then from ?

I will take a look and see if i can build them and tell you how i did it.

Kind regards

Here you go, not sure which architecture to use i'm using 64bit ubuntu
[http://www.archlinux.org/packages/extra/i686/glew/](http://www.archlinux.org/packages/extra/i686/glew/)
[http://www.archlinux.org/packages/extra/x86_64/glew/](http://www.archlinux.org/packages/extra/x86_64/glew/)

---

### Post by matt_symes on 2012-07-04
Hi

Why are you looking at the Arch packages instead of Ubuntu ? There is a Ubuntu package available here.

[https://launchpad.net/ubuntu/+source/glew](https://launchpad.net/ubuntu/+source/glew)

Version [1.7.0-3]("https://launchpad.net/ubuntu/+source/glew/1.7.0-3").

Have you checked to see if it is in the repo's. Open a terminal and type

```
apt-cache search glew
```Please post back the results here as i am not in my Ubuntu distribution at the moment, but in Fedora, so i cannot check for you.

If it's not in the repos then you will need to download the source for your Ubuntu version and then you will need to build it.

Do you need help building it for Ubuntu (as you were looking at the Arch packages before), if it's not in the repos ? If you do then post back.

Kind regards

---

### Post by einstein**-7 on 2012-07-06
Thanks! used your links and finally found the .deb installers and installed it that way.
As for the repos they only showed up to version 1.6.  Just curious though what the general compiling process would be if i'd downloaded the source.  Might have to do it one day and i don't have a clue as to how.

---

### Post by matt_symes on 2012-07-08
Hi

> **einstein**-7 said:**
> Thanks! used your links and finally found the .deb installers and installed it that way.
As for the repos they only showed up to version 1.6.  Just curious though what the general compiling process would be if i'd downloaded the source.  Might have to do it one day and i don't have a clue as to how.

That very much depends on the package. Look for a file called README and other text files :)

Generally though...

```
./configure
```

```
make
```

```
sudo make install
```

Kind regard

---

