---
title: "jdk1.6 for ubuntu"
date: 2009-12-03
forum: General Help
---

### Post by ttsdinesh on 2009-12-03
Can somebody show me a link where i can download jdk1.6 for ubuntu. I downloaded java_ee_sdk-5_08-jdk-6u17-linux.bin from sun.com. It is around 164MB. But i cant install that package in Ubuntu. I am using Ubuntu 9.04.

---

### Post by jbrown96 on 2009-12-03
You don't need to download anything from Sun. One of the great benefits of Linux is that there is package management, which is used to install practically any software you may need. You can use apt-get, which is a terminal utility to install applications or Synaptic which is a grpahical utitity. 

To use Synaptic:
System-->Administration-->Synaptic. Search for sun-java6-sdk and install it.

To use apt-get:
Applications-->Accessories-->Terminal then run ```
sudo apt-get install sun-java6-sdk
```

---

### Post by Ancanus on 2009-12-03
> **ttsdinesh said:**
> Can somebody show me a link where i can download jdk1.6 for ubuntu. I downloaded java_ee_sdk-5_08-jdk-6u17-linux.bin from sun.com. It is around 164MB. But i cant install that package in Ubuntu. I am using Ubuntu 9.04.

Have you tried downloading it from the repositories?

```
sudo aptitude install sun-java6-jdk
```OR
```

sudo aptitude install openjdk-6-jdk
```

---

### Post by doas777 on 2009-12-03
if you opt for sun java, you need to run this command to tell ubuntu to use the sun compiler/runtime by default:

```
sudo update-java-alternatives -s java-6-sun
```

---

### Post by ttsdinesh on 2009-12-03
Actually i am unable to connect internet via Ubuntu. My modem is not detected in Ubuntu.:( So i have to download java using XP and install it in Ubuntu. So i need some solid link to download the package.

---

### Post by jbrown96 on 2009-12-03
> **ttsdinesh said:**
> Actually i am unable to connect internet via Ubuntu. My modem is not detected in Ubuntu.:( So i have to download java using XP and install it in Ubuntu. So i need some solid link to download the package.

Gotcha. Open a terminal (apps-->accessories), then run ```
chmod u+x /path/to/java.bin
``` and then install with ```
/path/to/java.bin
``` I have not installed it this way; you might need to run it with root privileges, so you can run ```
sudo !!
``` and it will execute the previous command with the proper permissions.

---

### Post by ttsdinesh on 2009-12-03
I am running Ubuntu under VMWare. When i run > chmod u+x /path/to/java.bin it produces the following error "No such file or directory".

---

### Post by jbrown96 on 2009-12-03
you need to change /path/to/java.bin to the actual file path. You probably downloaded it to your Desktop (default location for firefox), so the path would be ./Desktop/java_ee_sdk-5_08-jdk-6u17-linux.bin but it may be different if you saved it somewhere else.

---

