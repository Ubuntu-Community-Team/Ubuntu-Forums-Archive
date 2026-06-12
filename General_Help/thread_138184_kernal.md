---
title: "kernal"
date: 2006-03-01
forum: General Help
---

### Post by harley on 2006-03-01
does ubuntu install the kernal sorces by default or do i have to do it and if so how do i find my kernal version and install the sorce?

---

### Post by jeremiebergeron on 2006-03-01
It does not do it by default so you do have to install them. I believe you can install them using: apt-get install linux-source-2.6.12

Also, one easy way to check your kernel version is using the command: uname -r

Cheers.

---

### Post by mostwanted on 2006-03-01
Ubuntu doesn't come with any source in the default install. I guess you could do an

```
apt-get source [my_kernel_image]
```

for Ubuntu specific source.

---

### Post by christhemonkey on 2006-03-01
```
uname -a
```
That tells you lots of things about your system, one of them being your kernel version.
Ubuntu has the kernel sources in the repositories but they are quite a while behind vanilla kernels (understandably though).

---

### Post by harley on 2006-03-01
[QUOTE=mostwanted]Ubuntu doesn't come with any source in the default install. I guess you could do an

```
apt-get source [my_kernel_image]
```

for Ubuntu specific source.[/QUOTE]
do i type my version in between the brackets ?

---

### Post by Ramses de Norre on 2006-03-01
```
sudo apt-get install linux-source-2.6.12
```
for example

---

### Post by harley on 2006-03-01
im fairly new to linux so im still trying to understand..i just download a linux kernal source patch and did a  ./patch  and it said permission denied any idea why?
i only have 1 user myself do i need to login under root and if so i tried to do that and i typed root for the username but i do not know the root password , and i have not made one so if i need to log in under root how do i ?

---

### Post by harley on 2006-03-01
[QUOTE=Ramses de Norre]```
sudo apt-get install linux-source-2.6.12
```
for example[/QUOTE]

ok that download and unpacked 

do i need to do anything else like make or make install ?

---

### Post by Ramses de Norre on 2006-03-01
apt-get install installs it:) logic;)

And you don't need to log in as root, use sudo in front of your command and type your own password.

---

### Post by harley on 2006-03-01
how do i find out what other packages are installed ? is there a log file?

---

