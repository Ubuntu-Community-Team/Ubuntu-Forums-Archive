---
title: "Flash Plugin"
date: 2010-07-19
forum: General Help
---

### Post by zombrax on 2010-07-19
G'day,

Just been trying to install flash player for playing vids etc via facebook and getting the msg of "Flash Player needs to be installed"

However when trying to install it via 
sudo apt-get install adobe-flashplugin

I get the msg of "package not available, but is referred to by another package"

Tried to get it through APT and get "adobe-flashplugin" is virtual

Also tried deb and get this error msg "Error: Wrong architecture 'i386'

Could someone please try and help me?

Running Lucid Server with desktop installed as well on BenQ Joybook S42 Laptop.

Thanks in advance.

---

### Post by spcwingo on 2010-07-19
Post the output of this command:

```
uname -a
```

---

### Post by zombrax on 2010-07-19
Linux Hyp3r 2.6.32-23-server #37-Ubuntu SMP Fri Jun 11 09:11:11 UTC 2010 x86_64 GNU/Linux

---

### Post by cavalier911 on 2010-07-19
64 Bit:
[https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins](https://help.ubuntu.com/community/AMD64/FirefoxAndPlugins)

---

### Post by QIII on 2010-07-19
Using the 64 bit Linux version is NOT ADVISABLE at this time.  As a matter of fact, it is unsupported by Adobe for the time being.

[http://labs.adobe.com/technologies/flashplayer10/64bit.html](http://labs.adobe.com/technologies/flashplayer10/64bit.html)

Not only was it a beta and a resource hog, it suffered from some significant security issues found in the 32 bit version that was updated.

For the time being, use the 32 bit version found in the repos.

---

### Post by cavalier911 on 2010-07-19
```
sudo apt-get install flashplugin-installer
```

---

### Post by lovinglinux on 2010-07-20
Get version 1.0.8 of my extension [FLASH-AID](http://flash-aid-extension.blogspot.com), it will take care of removing possible conflicting plugins and install the proper flash version.

You are having trouble with **adobe-flashplugin** because it is in the partner repository, which is not enabled by default. The **flashplugin-installer** is essentially the same thing.

---

### Post by zombrax on 2010-07-20
Thanks guys! Problem solved!

Again a wonderful bunch of people helping each other :)

---

