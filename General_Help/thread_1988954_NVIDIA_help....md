---
title: "NVIDIA help..."
date: 2012-05-28
forum: General Help
---

### Post by SuzanneLP on 2012-05-28
Hello!

I'm new at Linux and don't know much about computers. Had trouble installing Ubuntu on my pc and after a lot of research and reading, I found out that it's because of NVIDIA... I've managed to finally install Ubuntu and downloaded the driver for NVIDIA... my problem is that I really don't know how to install the new NVIDIA drivers and always need to start on "nomodeset"... can someone guide me step by step how to install the drivers please? 

Thanks in advance!

---

### Post by victor.zamanian on 2012-05-28
The following community documentation on this subject might help you.

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

---

### Post by pbrane on 2012-05-28
Another option to installing the nvidia drivers is to use the x-swat ppa
[https://launchpad.net/~ubuntu-x-swat/+archive/x-updates]("https://launchpad.net/~ubuntu-x-swat/+archive/x-updates")

This will install and update the latest stable nvidia drivers. I use this ppa and it works great and can be trusted.

since nouveau drivers have become the default it can be a hassle to install the binary drivers from nvidia. Having that driver packaged for ubuntu is a better way to install them.

you can install the x-swat ppa by typing this in a terminal
```

sudo add-apt-repository ppa:ubuntu-x-swat/x-updates

```

---

