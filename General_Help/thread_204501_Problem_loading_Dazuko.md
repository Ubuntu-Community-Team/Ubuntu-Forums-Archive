---
title: "Problem loading Dazuko"
date: 2006-06-27
forum: General Help
---

### Post by snl on 2006-06-27
I am trying to Dazuko and AntiVir following the guide here

[http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php]("http://allyourtech.com/content/articles/15_01_2006_installing_antivir_with_on_access_scanning_in_ubuntu_linux.php")

I managed to install Dazuko but is having problem loading it.

```
snl@R100:~$ sudo rmmod capability
snl@R100:~$ sudo modprobe dazuko
FATAL: Error inserting dazuko (/lib/modules/2.6.15-25-686/kernel/dazuko/dazuko.ko): Invalid module format
```

Please help.
Thank you.

---

### Post by ce41635 on 2007-01-04
I Have the same problem with Ubuntu Edgy. Do you find a the solution for your problem ?

---

### Post by danieleb on 2007-06-10
try to download the latest version of dazuko, i'm using it with clamav and it works properly in the way you use it..

---

### Post by murmelhunter on 2007-07-01
1. install via synaptic package manager the following: module-assistant

2. open the terminal and type now:

sudo m-a a-i dazuko

3. do the a test while typing now in the terminal:

sudo modprobe -r capability
sudo modprobe dazuko
sudo modprobe capability


If you have the Guard already install that you will be able to use it now

---

### Post by rlozano on 2007-07-18
> **murmelhunter said:**
> 1. install via synaptic package manager the following: module-assistant

2. open the terminal and type now:

sudo m-a a-i dazuko

3. do the a test while typing now in the terminal:

sudo modprobe -r capability
sudo modprobe dazuko
sudo modprobe capability


If you have the Guard already install that you will be able to use it now

but how do you make it start automatically? this means that everytime you start your machine, you need to issue those command right?

---

