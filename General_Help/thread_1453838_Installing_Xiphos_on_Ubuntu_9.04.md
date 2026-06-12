---
title: "Installing Xiphos on Ubuntu 9.04"
date: 2010-04-13
forum: General Help
---

### Post by Rick B. on 2010-04-13
Can anyone out there give me SIMPLE step-by-step instructions to install Xiphos on Ubuntu 9.04? Thanks in advance.

Rick Beltz

---

### Post by zvacet on 2010-04-14
[Here]("https://edge.launchpad.net/~pkgcrosswire/+archive/ppa")

---

### Post by Rick B. on 2010-04-14
What is the name of the file to download for 9.04 and where is the step by step procedure for installing it? I've tried many things but nothing has worked so far. Thanks.

---

### Post by zvacet on 2010-04-14
In **applications>accessories>terminal** type


```
gksudo gedit /etc/apt/sources.list
```

add this line to your source list

deb [http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu](http://ppa.launchpad.net/pkgcrosswire/ppa/ubuntu) jaunty main 

save and close file.After this type 

sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 287A2031

when it is finish type

```
sudo apt-get update
```

Go in system>administration>synaptic and find your package there and install it from there.

---

