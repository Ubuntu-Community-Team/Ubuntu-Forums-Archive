---
title: "Installing abgx"
date: 2012-01-05
forum: General Help
---

### Post by Nabeel Abbas on 2012-01-05
I am trying to install abgx on my ubuntu 10.10 machine. However when i extract the tar ball, and run ./configure I get the following error. 

```
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
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
checking how to run the C preprocessor... gcc -E
checking for grep that handles long lines and -e... /bin/grep
checking for egrep... /bin/grep -E
checking whether gcc needs -traditional... no
checking for crc32 in -lz... no
configure: error: "zlib not found!"

```

---

### Post by conradin on 2012-01-06
I would look for zlib in the ubuntu software centre and try
```
sudo apt-get install zlibc
```

---

