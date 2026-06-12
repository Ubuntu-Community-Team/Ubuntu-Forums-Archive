---
title: "playOnlinux demands 3d acceleration"
date: 2010-05-04
forum: General Help
---

### Post by mIXpRo on 2010-05-04
hi there ,

i've installed playonlinux on my system ubuntu 10.04 , and it says that 3d acceleration aren't enabled , how can i do that , thnx in advance 
[FONT=monospace]
[/FONT]this is the output of :
lspci | grep VGA
VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)

---

### Post by Avoozl on 2010-05-12
I had the same message, but after I did:

```
sudo apt-get install mesa-utils
```

And then:

```
glxinfo | grep rendering
```

It returned "direct rendering: Yes" and after running PlayOnLinux again I did not get the message any more.

---

### Post by willz06jw on 2010-06-19
That worked for me, thanks!

---

### Post by syednizamudeen on 2010-07-21
Thanks mate...

---

### Post by &#1581;&#1587;&#1575;&#1606; on 2011-06-18
hello
i got this

# sudo apt-get install mesa-utils
Reading package lists... Done
Building dependency tree       
Reading state information... Done
mesa-utils is already the newest version.
mesa-utils set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

# glxinfo | grep rendering
Error: API mismatch: the NVIDIA kernel module has version 270.41.06,
but this NVIDIA driver component has version 270.41.19.  Please make
sure that the kernel module and all NVIDIA driver components
have the same version.
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

what should i do to get it works

---

