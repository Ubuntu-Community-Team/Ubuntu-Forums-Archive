---
title: "Bad driver install keeps popping up when installing new things."
date: 2011-08-31
forum: General Help
---

### Post by timbaah on 2011-08-31
Hello all!

I just installed ubuntu, kind of new to it..
But I know my way around terminal and stuff a little..

But now I got into this strange problem:

I installed drivers for my external USB sound card by Hercules ( DJ console remix )
And the installation didn't went really well.. The sound actually works, probably it did already before I installed the drivers, but I did the install because I though I needed to before checking if I had any sound.. ( Maybe it's the driver that made it work, I don't know )

And now anytime I install anything this errors turn up: 

```

Processing triggers for man-db ...
Setting up hdjmod-dkms (1.28) ...
Loading new hdjmod-1.28 DKMS files...
Error! Cannot locate /usr/src/hdjmod-1.28.dkms.tar.gz.
File does not exist.
dpkg: error processing hdjmod-dkms (--configure):
 subprocess installed post-installation script returned error exit status 2
Setting up fxload (0.0.20081013-1ubuntu1) ...
Setting up midisport-firmware (1.2+dsfg1-0ubuntu6) ...
Errors were encountered while processing:
 hdjmod-dkms
E: Sub-process /usr/bin/dpkg returned an error code (1)

```So my question to you ubuntu users is:
How can I get rid of the installation, or just get rid of the errors? 
These are certainly the errors from the Hercules driver installation, I'm sure!

Whenever I install anything they pop-up.
The software installs right, but it's just really annoying.. 

Hope you understand the problem, and can point me in a right direction to get rid of it..

Thanks!

---

### Post by jfed on 2011-08-31
Not too sure to be honest, but what you could do is install programs from the GUI from now on. 

Go to the Ubuntu Software Manager and download/install packages using that, or go to System>Administration and Synaptic Package manager to install them.

Alternatively you can try to uninstall the drivers for your sound card and see if the problem goes away.

---

### Post by timbaah on 2011-08-31
> **jfed said:**
>  or go to System>Administration and Synaptic Package manager to install them.

Didn't know about this feature of ubuntu, thanks for pointing that out!

---

### Post by timbaah on 2011-09-01
Guess I have to reinstall the system.. I want to go with Ubuntu Studio anyway.. :)

---

### Post by timbaah on 2011-09-26
I just removed the package with apt-get..

```
sudo apt-get remove hdjmod-dkms
```

---

