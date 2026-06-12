---
title: "32 bit Java on a 64 bit oneiric"
date: 2011-10-20
forum: General Help
---

### Post by lykwydchykyn on 2011-10-20
I run 64 bit Oneiric, but I have some important applications that require 32-bit java.

In the past, I'd install ia32-sun-java6-bin, and that took care of it.

Now, of course, licensing has changed and only openjdk is in the repos.  Also, with the switch to multiarch support, I'm not sure how I can have both 64bit and 32bit openjdk installed.

I tried installing the i386 version of openjdk alongside the amd64 package, but they conflict with each other and a whole bunch of important packages.

How can I do this?

---

### Post by searchfgold6789 on 2011-10-20
Actually, Sun Java *is* available from the repos.
EDI: Nvm it isn't! Follow guide here maybe: [http://askubuntu.com/questions/52154/how-do-i-install-the-latest-version-of-sun-java-in-ubuntu-11-10](http://askubuntu.com/questions/52154/how-do-i-install-the-latest-version-of-sun-java-in-ubuntu-11-10)

---

### Post by lykwydchykyn on 2011-10-20
> **searchfgold6789 said:**
> Actually, Sun Java *is* available from the repos.

Not in my repos.  And yes, I have partner repos enabled.

---

### Post by searchfgold6789 on 2011-10-20
You could still manually download and install it from their website. Also you could add the Natty restricted repository.```

sudo add-apt-repository "deb http://archive.canonical.com/ natty partner" 
sudo apt-get update 
sudo apt-get install sun-java6-plugin
```

---

### Post by lykwydchykyn on 2011-10-20
Well, yes; currently I still have the natty packages installed.  But the purpose of this thread is that I want to know what I'm supposed to do for the future.  I'm not clear on the point of this new multi-arch setup if I can't install i386 versions of packages alongside the 64bit.

---

### Post by lunarcloud on 2011-12-19
I'm also having issues. I really need to do this to cross-compile 32bit packages on 64bit. I need it for the libjvm.so file- so it's not just being picky.

```
sudo apt-get install --no-install-recommends openjdk-6-jre-headless:i386
```

Results in

```
$ sudo apt-get install --no-install-recommends openjdk-6-jre-headless:i386
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 openjdk-6-jre-headless:i386 : Depends: openjdk-6-jre-lib:i386 (>= 6b23~pre11-0ubuntu1.11.10) but it is not installable
                               Depends: ca-certificates-java:i386 but it is not installable
                               Depends: java-common:i386 (>= 0.28) but it is not installable
E: Unable to correct problems, you have held broken packages.
```

---

### Post by Dry Lips on 2011-12-19
Is this of any help?

[https://launchpad.net/~ferramroberto/+archive/java]("https://launchpad.net/%7Eferramroberto/+archive/java")

[https://launchpad.net/~ferramroberto/+archive/java/+packages]("https://launchpad.net/%7Eferramroberto/+archive/java/+packages")


How to add PPA:
```

sudo add-apt-repository ppa:ferramroberto/java
sudo apt-get update
sudo apt-get install sun-java6-jdk sun-java6-plugin
```

---

