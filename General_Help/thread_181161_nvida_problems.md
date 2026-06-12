---
title: "nvida problems"
date: 2006-05-23
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-23
i have tried manny ways to install nvidia drivers and non of them seem to be working can ne 1 help me with this


this is the method i am using 
[http://ubuntuguide.org/#installnvidiadriver]("http://ubuntuguide.org/#installnvidiadriver")

and when i go 

```
 sudo apt-get install nvidia-glx
```


i get the following error does ne 1 know how to help me plz

```
Reading package lists... Done
Building dependency tree... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate

```

---

### Post by localzuk on 2006-05-23
Do you have the other repositories enabled as per [https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto) ?

---

### Post by LORD_PoLvO on 2006-05-23
hey thnx all the repos were off lol ima try the nvida drivers again.

---

### Post by LORD_PoLvO on 2006-05-23
arrrrrrr i got up to 


```
root@dappertest:/home/daniel# sudo nvidia-glx-config enable
sudo: nvidia-glx-config: command not found
root@dappertest:/home/daniel#

```



can sum 1 plz help me

---

### Post by localzuk on 2006-05-25
Hmm... That app should be installed in /usr/sbin by the nvidia-glx package. Are you sure it is installed?

---

### Post by tseliot on 2006-05-25
try with:
```
sudo nvidia-xconfig
```

---

