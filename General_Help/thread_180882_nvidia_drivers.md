---
title: "nvidia drivers"
date: 2006-05-23
forum: General Help
---

### Post by LORD_PoLvO on 2006-05-23
does ne1 know ho to or have a link to a how to to install nvida drivers?

---

### Post by frodon on 2006-05-23
[http://doc.gwos.org/index.php/Install_Nvidia_driver](http://doc.gwos.org/index.php/Install_Nvidia_driver)

---

### Post by LORD_PoLvO on 2006-05-23
tried that nad i got


```
daniel@dappertest:~$ sudo apt-get install nvidia-glx
Password:
Reading package lists... Done
Building dependency tree... Done
Package nvidia-glx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package nvidia-glx has no installation candidate
daniel@dappertest:~$

```


ne other way?


btw im using daper if that makes a difference

---

### Post by LORD_PoLvO on 2006-05-23
i herd there is a way u can do it in synaptic and then change a text file to make it owrk ?

---

### Post by tseliot on 2006-05-23
This is my guide for Breezy:
[http://www.ubuntuforums.org/showthread.php?t=75074]("http://www.ubuntuforums.org/showthread.php?t=75074")

This one is for Dapper:
[http://www.ubuntuforums.org/showthread.php?t=139264]("http://www.ubuntuforums.org/showthread.php?t=139264")

This is the link to my scripts (which automate Method 2):
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html]("http://www.albertomilone.eu/europeo/nvidia_scripts1.html")

---

### Post by frodon on 2006-05-23
Doing that in synaptic would be exactly the same, however maybe you have some missing repositories in your sources.list file and it's why your system don't find the nvidia-glx package.
Could you post your sourcces.list file : ```
sudo gedit /etc/apt/sources.list

```

---

### Post by LORD_PoLvO on 2006-05-23
arg didnt work plz ne1 with the synaptic one the apt one never works i always getting errors on the first step..... last time i did it i did it in synaptic and configured xorg it was verry easy.

---

### Post by frodon on 2006-05-23
Again synaptic and apt commands are the same thing, synaptic is just a front-end for apt commands.
For sure the tseliot's guide works for dapper try it, the link i gave you was for breezy so i'm not sure it works for dapper.

**But you must have enable the needed repositories**

The Tseliot's guide is here : [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

Another link : 
[http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29](http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_Graphics_Driver_.28NVIDIA.29)

---

