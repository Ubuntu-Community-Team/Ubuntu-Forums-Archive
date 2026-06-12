---
title: "Developers packages"
date: 2010-09-02
forum: General Help
---

### Post by doriad on 2010-09-02
Hi all,

I'm a Fedora guy, but I thought I'd give Ubuntu a shot. When you install Fedora there is an option to install "Developers packages". I did not see such an option while installing Ubuntu. I am having a couple of issues:

1) I am trying to build open source project that I use all the time, but I'm getting a basic error:

```

error: iostream.h: No such file or directory

```

I installed glibc*, gcc* and g++ to no avail. I also installed kdevplat*, but the error persists. Which package am I missing?

2) I am trying to install boost:
```

doriad@davidlaptop:~/bin/VTK$ sudo apt-get install libboost-*
The following packages have unmet dependencies:
  libboost-mpi-dev: Depends: libboost-mpi1.40-dev but it is not installable
E: Broken packages

```

I haven't done anything except use apt-get install, so I can't imagine there should be any conflicts?

Thanks,

David

---

### Post by doriad on 2010-09-23
Any thoughts on this?

Thanks,

David

---

### Post by alphacrucis2 on 2010-09-23
> **doriad said:**
> Any thoughts on this?

Thanks,

David

Try installing the build-essential packgage first. 

```

sudo dpkg --configure -a
sudo apt-get install build-essential
```

---

### Post by doriad on 2010-09-23
Hm, it seems like it is already installed?

```

doriad@davidlaptop:~$ sudo dpkg --configure -a
doriad@davidlaptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  python-beagle linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
doriad@davidlaptop:~$ 

```

David

---

### Post by alphacrucis2 on 2010-09-23
> **doriad said:**
> Hm, it seems like it is already installed?

```

doriad@davidlaptop:~$ sudo dpkg --configure -a
doriad@davidlaptop:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
The following packages were automatically installed and are no longer required:
  python-beagle linux-headers-2.6.32-21 linux-headers-2.6.32-21-generic
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
doriad@davidlaptop:~$ 

```

David

Uggh! This might be your problem:

> [https://bugs.launchpad.net/ubuntu/+source/boost-defaults/+bug/531973](https://bugs.launchpad.net/ubuntu/+source/boost-defaults/+bug/531973)

---

### Post by doriad on 2010-09-24
1) Just curious, what makes you think that I have a Boost problem from the output I sent?

2) It says at the bottom the link you sent that it has been fixed. What do I need to do to get this working?

Thanks,

David

---

### Post by lloyd_b on 2010-09-24
> **doriad said:**
> Hi all,

I'm a Fedora guy, but I thought I'd give Ubuntu a shot. When you install Fedora there is an option to install "Developers packages". I did not see such an option while installing Ubuntu. I am having a couple of issues:

1) I am trying to build open source project that I use all the time, but I'm getting a basic error:

```

error: iostream.h: No such file or directory

```

I installed glibc*, gcc* and g++ to no avail. I also installed kdevplat*, but the error persists. Which package am I missing?

2) I am trying to install boost:
```

doriad@davidlaptop:~/bin/VTK$ sudo apt-get install libboost-*
The following packages have unmet dependencies:
  libboost-mpi-dev: Depends: libboost-mpi1.40-dev but it is not installable
E: Broken packages

```

I haven't done anything except use apt-get install, so I can't imagine there should be any conflicts?

Thanks,

David
The root problem is that "iostream.h" has been deprecated for quite some time, and appears to have finally disappeared from Ubuntu.

Is there a reason you're using "#include <iostream.h>", and not "#include <iostream>"?

Lloyd B.

---

### Post by doriad on 2010-09-24
I use several large libraries that rely on these files (VTK is the current one I'm trying to compile). Surely there are are compat packages I can install to get these files? It doesn't make sense that someone couldn't compile VTK on Ubuntu. In fact, I know many people who do, so I bet there is just a package I am missing.

David

---

### Post by doriad on 2010-10-30
Any more ideas?

---

### Post by doriad on 2011-01-07
Ok folks, we got this figured out.

I had to add:
```

export CPLUS_INCLUDE_PATH=$CPLUS_INCLUDE_PATH:/user/include/c++/4.4

```

to my .bashrc. 

Be careful though - if you are using CMake, you have to completely delete the build directory if you have run CMake without this line. When you recreate the build directory and try to build again, it will work!

---

