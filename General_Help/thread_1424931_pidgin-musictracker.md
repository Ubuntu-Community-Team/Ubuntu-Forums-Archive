---
title: "pidgin-musictracker"
date: 2010-03-08
forum: General Help
---

### Post by nos09 on 2010-03-08
how to install pidgin-musictracker plugin 
i tired this 
> 
codename-nos@codename-nos-desktop:~$ cd '/home/codename-nos/Downloads/pidgin-musictracker-0.4.21' 
codename-nos@codename-nos-desktop:~/Downloads/pidgin-musictracker-0.4.21$ ./configure --prefix=/usr make
configure: WARNING: you should use --build, --host, --target
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for make-gcc... no
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking build system type... Invalid configuration `make': machine `make' not recognized
configure: error: /bin/bash config/config.sub make failed
codename-nos@codename-nos-desktop:~/Downloads/pidgin-musictracker-0.4.21$ sudo make install
make: *** No rule to make target `install'.  Stop.
codename-nos@codename-nos-desktop:~/Downloads/pidgin-musictracker-0.4.21$ 


help me

---

### Post by LowSky on 2010-03-08
```
sudo apt-get install pidgin-musictracker
```

---

