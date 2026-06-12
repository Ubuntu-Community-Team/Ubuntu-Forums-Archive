---
title: "How to verify PAE extensions are loaded"
date: 2010-06-03
forum: General Help
---

### Post by KayakJim on 2010-06-03
I just installed Ubuntu 10.04 32-bit Desktop on a friend's computer. The computer has 4GB of RAM but the system is only showing 3GB total. This leads me to believe the PAE extensions are not loaded.

How can I verify that the PAE extensions are loaded and if they are not get them installed?

If you have another idea as to why the system would be short 1GB of RAM I would be open to that as well.

---

### Post by KayakJim on 2010-06-03
I found out that the following will install the PAE extensions but still do not know how to verify that they are actually installed.

```
sudo aptitude install linux-image-generic-pae
```

---

### Post by Ozymandias_117 on 2010-06-03
Pretty sure ```
uname -r
``` it should be 2.6.*-*-generic-pae I think the ones that end in -server also have pae

---

### Post by 3rdalbum on 2010-06-03
> **KayakJim said:**
> I found out that the following will install the PAE extensions but still do not know how to verify that they are actually installed.

```
sudo aptitude install linux-image-generic-pae
```

You answered your own question - System Monitor will show close to 4 GiB of RAM if PAE is enabled.

---

### Post by KayakJim on 2010-06-03
Thanks for the pointers to uname and System Monitor!

---

### Post by KayakJim on 2010-06-03
While browsing the web I came across the following command for enabling PAE extensions:

```
sudo sudo aptitude install linux-headers-server linux-image-server linux-server
```

So the questions now are:

1. What is the actual difference between the above command and the one in post #2?

2. Which one is better and can you provide an explanation as to why it is better?

---

### Post by KayakJim on 2010-06-03
For anyone that is interested, according to [this page]("https://help.ubuntu.com/community/EnablingPAE"), the command:

```
sudo sudo aptitude install linux-headers-server linux-image-server linux-server
```
is for Ubuntu versions prior to 9.10 Karmic, while the command:

```
sudo aptitude install linux-image-generic-pae
```
is for Ubuntu version 9.10 Karmic and 10.04 Lucid.

---

### Post by ShadowTek on 2010-06-03
I also have 4 GBs of RAM, and only 3.2 is being recognized, and the kernel does not have the "PAE" suffix.

According to the following, PAE is supposed to be enabled by default in 10.04:
"Both the CD and DVD installer of Ubuntu 10.04 automatically installs the PAE enabled kernel if it detects more than 3 Gb of available memory. In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages are not present on the CD."
[https://help.ubuntu.com/community/EnablingPAE](https://help.ubuntu.com/community/EnablingPAE)

I installed using the alternate CD. Did that have something to do with it?
(ubuntu-10.04-alternate-i386.iso)

---

### Post by KayakJim on 2010-06-03
The catch is the last sentence of that statement:

> In the case of the liveCD, a working network connection is required, since the PAE enabled kernel packages are not present on the CD.

If the installer wasn't able to get a internet connection to download the PAE packages then it didn't happen.

Running ```
sudo aptitude install linux-image-generic-pae
``` should fix you up just as it did me.

---

### Post by ShadowTek on 2010-06-03
> **KayakJim said:**
> If the installer wasn't able to get a internet connection to download the PAE packages then it didn't happen.
I *did* have an active connection during install. The server must have been unresponsive to the connection attempt.

Regardless, I think some sort of message should notify the user of the failure to successfully install PAE.

> Running ```
sudo aptitude install linux-image-generic-pae
``` should fix you up just as it did me.Yes, that works. I had to reinstall the nVidia drivers, but that was the only problem.

---

### Post by KayakJim on 2010-06-03
> **ShadowTek said:**
> Regardless, I think some sort of message should notify the user of the failure to successfully install PAE.

Agreed. I would have not known I was "missing" RAM had I not run the "free" command and noticed the discrepancy.

---

