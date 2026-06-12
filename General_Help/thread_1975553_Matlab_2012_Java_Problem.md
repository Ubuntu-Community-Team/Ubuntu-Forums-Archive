---
title: "Matlab 2012 Java Problem"
date: 2012-05-07
forum: General Help
---

### Post by SAAlqallaf on 2012-05-07
Hi all, 

I tried to install Matlab 2012 on ubuntu 10.04 Lts but, after installation I tried to run the ./install file and I get the following Java Error:
 
```
ahmed@ahmed-laptop:/usr/local/MATLAB/R2012a$ ./install 
Preparing installation files ...
cp: cannot stat `/usr/local/MATLAB/R2012a/bin/glnx86/libpng.so': No such file or directory
Installing ...
Exception in thread "main" java.lang.NoClassDefFoundError: com/mathworks/professionalinstaller/Launcher
Caused by: java.lang.ClassNotFoundException: com.mathworks.professionalinstaller.Launcher
    at java.net.URLClassLoader$1.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at java.lang.ClassLoader.loadClassInternal(Unknown Source)
Could not find the main class: com/mathworks/professionalinstaller/Launcher.  Program will exit.
Finished
```
I installed Java 6, and tried again and no luck...

---

### Post by georgelappies on 2012-05-07
Not directly related to your exact problem but have you tried using gnu octave instead of matlab?

Personally I have had much success using octave and it is compatible with matlab.

---

### Post by soumyabratapaul on 2012-05-07
> **SAAlqallaf said:**
> Hi all, 

I tried to install Matlab 2012 on ubuntu 10.04 Lts but, after installation I tried to run the ./install file and I get the following Java Error:
 
```
ahmed@ahmed-laptop:/usr/local/MATLAB/R2012a$ ./install 
Preparing installation files ...
cp: cannot stat `/usr/local/MATLAB/R2012a/bin/glnx86/libpng.so': No such file or directory
Installing ...
Exception in thread "main" java.lang.NoClassDefFoundError: com/mathworks/professionalinstaller/Launcher
Caused by: java.lang.ClassNotFoundException: com.mathworks.professionalinstaller.Launcher
    at java.net.URLClassLoader$1.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    at java.net.URLClassLoader.findClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at sun.misc.Launcher$AppClassLoader.loadClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at java.lang.ClassLoader.loadClassInternal(Unknown Source)
Could not find the main class: com/mathworks/professionalinstaller/Launcher.  Program will exit.
Finished
```
I installed Java 6, and tried again and no luck...

The error looks like it cannot find the class Launcher. See if the class is there and the file is not corrupted!

---

### Post by steeldriver on 2012-05-07
I would think you need root permissions to run this install, no? try 

```
$ sudo ./install
```or (if it is a graphical install)

```
$ gksudo ./install
```

---

### Post by SAAlqallaf on 2012-05-07
Thanx for ur replies...

As for why matlab not octave... simply because of simulink capabilities "Simpower"

And I have tried doing it as root but no luck either. 

And I do not know how to check the class launcher....

---

### Post by Hannu Mikael on 2012-05-08
Oracle Java 7 update 4
(after installation reboot PC)

sudo add-apt-repository ppa:webupd8team/java
sudo apt-get update
sudo apt-get install oracle-java7-installer

---

### Post by SAAlqallaf on 2012-05-09
No luck either :confused:

---

### Post by elexhobby on 2012-05-12
Hi SAAlqallaf,

Were you able to find a solution? I'm facing the same problem as you.

---

### Post by aplomado on 2012-06-18
Hello,
  I was getting an error identical to yours (after the cannot stat line) when trying to install matlab 2012a on Ubuntu 12.04  using the command sudo ./install

However, using gksudo ./install resulted in a clean install without trouble (inspired by [steeldriver]("http://ubuntuforums.org/member.php?u=1627500")'s post)

I hope this works out

---

### Post by kalyp on 2012-08-21
Hello,

Same problem as SAAlqallaf with the same error. Anybody found the solution? Both sudo and gksudo give the same error unfortunately...
Thanks!

---

### Post by kalyp on 2012-08-21
Nevermind. I hadn't installed matlab in a while and when I saw an "install" file thought I had to run it. 
In my case, I just need to run bin/matlab and it works, no need for that install file (which wasn't in the previous years versions in my case). Since it's a company license though, it is probably preinstalled... 

> **kalyp said:**
> Hello,

Same problem as SAAlqallaf with the same error. Anybody found the solution? Both sudo and gksudo give the same error unfortunately...
Thanks!

---

### Post by rohit4 on 2013-08-20
Anybody found a solution to this problem yet ? please help me out , I'm stuck at the same point.
I have put up posts in other forums as well, but no progress as of now. 
HELP

---

### Post by naarkhoo on 2014-08-13
any update on this threat - I encounter the same error on matlab 2014a

---

