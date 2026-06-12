---
title: "Can't open Update Manager or Software Center, messed things up"
date: 2012-04-08
forum: General Help
---

### Post by coldjeanz on 2012-04-08
I was trying to install Beatbox on my 11.10 so I ran these in terminal

*[FONT=Liberation Serif]sudo add-apt-repository ppa:elementaryart/elementarydesktop[/FONT]*


*[FONT=Liberation Serif]sudo add-apt-repository ppa:nemequ/sqlheavy[/FONT]*


[I][FONT=Liberation Serif]
[/FONT][/I]
Didn't exactly work. Now when I try to open Update Manager I get this error:

[IMG]http://i.imgur.com/uHWgw.png[/IMG]

I'm tempted to just remove the elementary PPA I installed but I don't know if this would solve the issue.

---

### Post by Bucky Ball on 2012-04-08
Remove the PPA and see if it does. Then you can start afresh ...

---

### Post by coldjeanz on 2012-04-08
Removed it and still getting the error, only now it says it's on "Line 1" instead of "Line 3". Not sure what to do now.

The exact error now

> Could not initialize the package information

An unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:Type 'ain' is not known on line 1 in source list /etc/apt/sources.list.d/elementaryart-elementarydesktop-oneiric.list'

---

### Post by PhantomTurtle on 2012-04-08
The Elementary PPA worked fine for me. Which version of Ubuntu are you using. I was using 12.04 and Beatbox, pantheon and all those other elementary os programs installed fine for me. I would remove the ppa though, it seems to be what's causing the problem.

EDIT: Also, what is line 1, in your sources.list then. Which ppa is it?

---

### Post by coldjeanz on 2012-04-08
What does it mean by Line 1 though?

Edit: Ok now it's saying something like this error is probably caused by installing packages that do not have met dependencies

---

### Post by PhantomTurtle on 2012-04-08
Like line 3 was elementaryart-elementarydesktop-oneric.list. Which ppa does it say in update manager now?

---

### Post by coldjeanz on 2012-04-08
Ok some how I fixed it by redoing the steps necessary to install Beatbox, I can update and open software center so that headache is gone.

But I still can't install Beatbox lol, it says I'm missing these dependencies when I try to install it through Software Center

> The following packages have unmet dependencies:

beatbox: Depends: libc6 (>= 2.3.4) but 2.13-20ubuntu5.1 is to be installed
         Depends: libcairo2 (>= 1.2.4) but 1.10.2-6ubuntu3 is to be installed
         Depends: libgconf2-4 (>= 2.31.1) but 3.2.3-0ubuntu0.1 is to be installed
         Depends: libgdk-pixbuf2.0-0 (>= 2.22.0) but 2.24.0-1ubuntu1 is to be installed
         Depends: libgee2 (>= 0.5.0) but 0.6.2.1-0ubuntu1 is to be installed
         Depends: libglib2.0-0 (>= 2.28.0) but 2.30.0-0ubuntu4 is to be installed
         Depends: libgranite0 but it is not going to be installed
         Depends: libgstreamer-plugins-base0.10-0 (>= 0.10.12) but 0.10.35-1 is to be installed
         Depends: libgstreamer0.10-0 (>= 0.10.24) but 0.10.35-1 is to be installed
         Depends: libgtk-3-0 (>= 3.0.0) but 3.2.0-0ubuntu6 is to be installed
         Depends: libindicate5 (>= 0.4.90) but 0.6.1-0ubuntu1 is to be installed
         Depends: libnotify4 (>= 0.7.0) but 0.7.4-1 is to be installed
         Depends: libpango1.0-0 (>= 1.14.0) but 1.29.3+git20110916-0ubuntu1 is to be installed
         Depends: libsoup2.4-1 (>= 2.25.2) but 2.36.0-0ubuntu1 is to be installed
         Depends: libtagc0 (>= 1.5) but 1.7-1 is to be installed
         Depends: libxml2 (>= 2.7.4) but 2.7.8.dfsg-4ubuntu0.2 is to be installed
         Depends: libzeitgeist-1.0-1 (>= 0.3.2) but 0.3.12-0ubuntu1 is to be installed


---

### Post by Bucky Ball on 2012-04-08
Try:

```
sudo apt-get update
```

Ignore errors. Then:

```
sudo apt-get upgrade
```

(This will hopefully upgrade dependencies; it WON'T upgrade the release), Then:

```
sudo apt-get update
```

... again.

---

