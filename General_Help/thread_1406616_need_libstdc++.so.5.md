---
title: "need libstdc++.so.5"
date: 2010-02-14
forum: General Help
---

### Post by Rymer on 2010-02-14
I'm trying to install **java_ee_sdk-5_08-jdk-6u18-linux-ml.bin**, but it asks me for **libstdc++.so.5** library. I've searched for it on my filesystem, and there is no such library. 
**sudo apt-get install libstdc++5** does not wokrs too for me(
Here is a full log:
```
dwarf@Nasekomaya:~/Downloads$ sudo ./java_ee_sdk-5_08-jdk-6u18-linux-ml.bin
./java_ee_sdk-5_08-jdk-6u18-linux-ml.bin: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory
dwarf@Nasekomaya:~/Downloads$ sudo apt-get install libstdc++5
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package libstdc++5 is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package libstdc++5 has no installation candidate
```
How can this problem be solved?

---

### Post by mc4man on 2010-02-14
you may download and install the jaunty package, it will install cleanly though whether it will work out you won't know till you try....

[http://packages.ubuntu.com/en/jaunty/libstdc++5](http://packages.ubuntu.com/en/jaunty/libstdc++5)

---

### Post by rnerwein on 2010-02-14
hi
if you can't fix it fake it
create a symbolic link from libstdc++.so.6 to  [B]libstdc++.so.5. i think this will work.
but look at the format of the lib ( file libstd....) for 32 or 64 bit.
ciao
[/B]

---

### Post by gansvv on 2010-07-10
No. They are different library versions. Thats not going to work!

> **rnerwein said:**
> hi
if you can't fix it fake it
create a symbolic link from libstdc++.so.6 to  [B]libstdc++.so.5. i think this will work.
but look at the format of the lib ( file libstd....) for 32 or 64 bit.
ciao
[/B]

You'll probably get errors such as:
 version `GLIBCPP_3.2' not found
 version `CXXABI_1.2' not found

---

### Post by gansvv on 2010-07-10
Use the download link from 
[http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download) and install.

E.g.:
```

wget http://ftp.us.debian.org/debian/pool/main/g/gcc-3.3/libstdc++5_3.3.6-18_i386.deb

sudo dpkg -i libstdc++5_3.3.6-18_i386.deb 

```

For 62bit: [http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

---

### Post by Das Goat on 2010-07-29
Here is the direct link:

[http://packages.debian.org/lenny/amd64/libstdc++5/download](http://packages.debian.org/lenny/amd64/libstdc++5/download)

Hope that helps.

---

### Post by Bimme on 2010-08-06
I guess that the best method would be to add deb
[http://cz.archive.ubuntu.com/ubuntu](http://cz.archive.ubuntu.com/ubuntu) jaunty main universe # (change cz to appropriate mirror)
to /etc/apt/sources.list and use apt or aptitude.
Please let me know if I'm wrong, but this is what I did and it seem to work great. Aptitude stopped complaining about some other packages too.

---

### Post by pendelton on 2011-01-01
The old Jaunty link doesn't seem to work. Try the following instead:

[http://packages.debian.org/lenny/i386/libstdc++5/download](http://packages.debian.org/lenny/i386/libstdc++5/download)

---

### Post by pendelton on 2011-01-01
Sorry, Das already posted this above.

---

