---
title: "Pan 0.134 install question"
date: 2011-03-19
forum: General Help
---

### Post by David D. on 2011-03-19
An update to the Pan Newsreader (0.134, "Wait for Me") is out as of February 15, 2011.  This release is supposed to add some functionality as well as some bug fixes.

Has anyone successfully installed from the source code?  I have tried, but have not been successful.  I get an error message about "GLIB" not being found.

Does anyone know a site for which a .deb file for this can be downloaded?

---

### Post by David D. on 2011-03-19
The install instructions say to use "./configure" to compile.  When I do so in terminal I get an error.  The error message say 
"checking for GLIB - version >= 2.14.0... no
*** Could not run GLIB test program, checking why...
*** The test program failed to compile or link. See the file config.log for the
*** exact error that occured. This usually means GLIB is incorrectly installed.

The applicable section of the config.log says 
"configure:6434: checking for GLIB - version >= 2.14.0
configure:6566: result: no
configure:6594: gcc -o conftest -g -O2    conftest.c   >&5
conftest.c:42: fatal error: glib.h: No such file or directory
compilation terminated."

What do I need to install to make this compile?

I get the same result in both 10.10 and in Natty.

---

### Post by David D. on 2011-03-21
Bump - any ideas?

---

### Post by qamelian on 2011-03-21
In a terminal, type:

```
sudo apt-get build-dep pan
```

This should install all of the build dependancies for compiling Pan from source. Providing none of the dependancy versions needed are newr than what is in the repos, you should be able to run ./configure no without any errors.

---

### Post by David D. on 2011-03-21
Thank you gamelian, I was able to install version 0.134 of Pan on my Natty test system.  I will try on my main system later.

Note for any others who want to update, I found that after running the code from gamelian and ./configure that I got another error about gmime.  By going into synaptic and installing libgmime2.4-cil-dev and libgmime2.4-dev I was able to run ```
./configure
``` and the ```
sudo make install 

``` with no further problems.

---

### Post by gatewayasteroid on 2011-04-14
> **David D. said:**
> An update to the Pan Newsreader (0.134, "Wait for Me") is out as of February 15, 2011.  This release is supposed to add some functionality as well as some bug fixes.

Has anyone successfully installed from the source code?  I have tried, but have not been successful.  I get an error message about "GLIB" not being found.

Does anyone know a site for which a .deb file for this can be downloaded?

[https://launchpad.net/~klaus-vormweg/+archive/ppa]("https://launchpad.net/~klaus-vormweg/+archive/ppa")

```
sudo add-apt-repository ppa:klaus-vormweg/ppa
```

Then 

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by nobrac on 2011-05-16
> **gatewayasteroid said:**
> [https://launchpad.net/~klaus-vormweg/+archive/ppa]("https://launchpad.net/~klaus-vormweg/+archive/ppa")

```
sudo add-apt-repository ppa:klaus-vormweg/ppa
```

Then 

```
sudo apt-get update
sudo apt-get upgrade
```


I satisfied all the library deps but pan still didn't want to build. I came back here looking for clues. And lo and behold, a PPA. Excellent. Thanks for the pointer.

---

