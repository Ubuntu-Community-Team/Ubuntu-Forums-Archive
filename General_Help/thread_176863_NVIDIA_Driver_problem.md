---
title: "NVIDIA Driver problem"
date: 2006-05-15
forum: General Help
---

### Post by Porky on 2006-05-15
Am runig a 64 system, whit a NVIDIA Geforce 7600GT and when i try to install NVIDIA driver i get this:
" ERROR: Unable to find the system utility `ld`; please make sure you have the package 'binutils' installed.  If you do have binutils installed,
then please check that `ld` is in your PATH." 
what dos this mean.

---

### Post by Sutekh on 2006-05-15
Which method are you trying?  

I would interpret the error to mean you need the binutils package. If you are using Method 2 from the NVIDIA HOWTO thread, you need the build-essential package, which should bring in the binutils package
```
sudo apt-get install build-essential
``` otherwise you can explicitly install the binutils package
```
sudo apt-get install binutils
```

---

