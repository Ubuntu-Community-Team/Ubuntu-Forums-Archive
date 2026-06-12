---
title: "Help installing an app"
date: 2012-02-04
forum: General Help
---

### Post by TimEnid on 2012-02-04
I am trying to install GeekBench, its a tar.gz file. the file is in my downloads directory. so in the terminal, i put 
```
cd home/tim/downloads
```
then 
```
tar -zxvf Geekbench-2.2.6-Linux.tar.gz
```
and i get
```
dist/Geekbench-2.2.6-Linux/
dist/Geekbench-2.2.6-Linux/geekbench_x86_64
dist/Geekbench-2.2.6-Linux/geekbench.plar
dist/Geekbench-2.2.6-Linux/geekbench_x86_32
```
i type 
```
./configure
```
but i get
```
bash: ./configure: No such file or directory
```

am i missing something?

---

### Post by aasdfasdfg on 2012-02-05
See [here]("http://support.primatelabs.ca/discussions/problems/469-geekbench-ubuntu") for their support. From your sig it looks like you're running on x86_64, so you'll need to install the 32-bit compatibility libs with
```
sudo apt-get install ia32-libs
```and then execute the ```
dist/Geekbench-2.2.6-Linux/geekbench_x86_64
```file. There is no "configure" file they provided; just run ```
./geekbench_x86_64
``` from the proper directory.

---

