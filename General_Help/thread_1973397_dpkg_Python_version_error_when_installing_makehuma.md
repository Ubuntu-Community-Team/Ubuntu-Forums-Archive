---
title: "dpkg Python version error when installing makehuman"
date: 2012-05-04
forum: General Help
---

### Post by Senior_Buckethead on 2012-05-04
Hello all, I am wanting to install a program called Makehuman. I downloaded the .deb file and went to install it:
```

glenn@acer:~/Downloads$ sudo dpkg -i makehuman-alpha_6_i386.deb
Selecting previously unselected package makehuman-alpha.
(Reading database ... 228616 files and directories currently installed.)
Unpacking makehuman-alpha (from makehuman-alpha_6_i386.deb) ...
dpkg: dependency problems prevent configuration of makehuman-alpha:
 makehuman-alpha depends on python2.6; however:
  Package python2.6 is not installed.
 makehuman-alpha depends on libglew1.5; however:
  Package libglew1.5 is not installed.
dpkg: error processing makehuman-alpha (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Errors were encountered while processing:
 makehuman-alpha
glenn@acer:~/Downloads$ 

```well, thats odd, since I have a later version of python:
```

glenn@acer:~/Downloads$ python --version
Python 2.7.3

```Can someone tell me why the installer has 'spit the dummy' over python when python's installed?

---

### Post by PhantomTurtle on 2012-05-04
It's because makehuman requires python 2.6. I actually don't know why it wouldn't work in python 2.7(I'm probably not the best person to ask about that). Also post around on the Makehuman forums, they might have some better answers.

EDIT: I was just looking at the makehuman website and it says this was built for Ubuntu 8.10, so it looks like it hasn't been tested on newer version of Ubuntu. Source: [http://www.makehuman.org/node/143](http://www.makehuman.org/node/143)

---

### Post by Senior_Buckethead on 2012-05-04
I followed the link to installing .deb versions of makehuman:
[http://www.makehuman.org/node/135](http://www.makehuman.org/node/135)
and got the same error message:

```

glenn@acer:~$ sudo apt-get install makehuman-nightly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 makehuman-nightly : Depends: python2.6 but it is not installable
                     Depends: libpython2.6 but it is not installable
                     Recommends: aqsis but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
glenn@acer:~$ 

```

Python is not installable? Not just not installed, but not installable..
Hmm

---

### Post by PhantomTurtle on 2012-05-04
> **Senior_Buckethead said:**
> I followed the link to installing .deb versions of makehuman:
[http://www.makehuman.org/node/135](http://www.makehuman.org/node/135)
and got the same error message:

```

glenn@acer:~$ sudo apt-get install makehuman-nightly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 makehuman-nightly : Depends: python2.6 but it is not installable
                     Depends: libpython2.6 but it is not installable
                     Recommends: aqsis but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
glenn@acer:~$ 

```

Python is not installable? Not just not installed, but not installable..
Hmm

It's not installable because libpython2.6 is not available in the repositories, because Ubuntu now uses python 2.7.

---

### Post by Senior_Buckethead on 2012-05-04
So, what is really saying is makehuman won't run on 12.04 because the python libraries upon which it depends are obsolete.

Is that correct?

---

### Post by PhantomTurtle on 2012-05-04
> **Senior_Buckethead said:**
> So, what is really saying is makehuman won't run on 12.04 because the python libraries upon which it depends are obsolete.

Is that correct?

Unfortunately, yes. It looks like a cool project though. First time I've ever heard of it. I was actually kinda hoping it would work.

---

### Post by knezmej on 2012-05-15
It will work if You do (not pretty sollution):
```

cd /usr/lib
sudo ln -s libpython2.7.so.1.0 libpython2.6.so.1.0
cd /usr/include
sudo ln -s python2.7 python2.6
```

---

### Post by Senior_Buckethead on 2012-05-15
Hey thanks Knezmej

Apologies for the dumb question. I see thats a symbolic link, but what is it achieving?

Glenn.

---

