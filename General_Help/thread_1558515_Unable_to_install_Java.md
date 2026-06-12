---
title: "Unable to install Java"
date: 2010-08-22
forum: General Help
---

### Post by type8code0 on 2010-08-22
Hi,

I'm having this problem when trying to install Java.. Please let me know if there is anything wrong with my command below.. or is there anything else I need to do.

Any help would be highly appreciated. Thanks :)

> type8code0@desktop:~$ sudo apt-get install sun-java6-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate
type8code0@desktop:~$ 

---

### Post by anirudhtomer on 2010-08-22
try some other package like open-jdk
see every package corresponds to an FTP site & if after some time that becomes unavailable u won't be able to download from there. I don't know the problem in your case but you can always download Java from other packages..

when you type "$ javac" it will show you command not found & also 6-7 packages from where u can download Java so try some other package

---

### Post by surfer on 2010-08-22
did you enable the partner repositories? if i'm not mistaken, sun-java is in there,

---

### Post by howefield on 2010-08-22
You'll find Sun Java by enabling the partner repository.

[https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun%20Java%20moved%20to%20the%20Partner%20repository](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Sun%20Java%20moved%20to%20the%20Partner%20repository)

The packages I install are sun-java6-jre sun-java6-plugin and sun-java6-fonts.

---

### Post by type8code0 on 2010-08-22
Thanks guys, I have found the same problem and solution here... and it fix the problem :)

[http://happy-coding.com/install-sun-java6-jdk-on-ubuntu-10-04-lucid/](http://happy-coding.com/install-sun-java6-jdk-on-ubuntu-10-04-lucid/)

> I just had trouble to install the Sun Java6 JDK after updating to Ubuntu 10.04. The problem was that the system couldn’t find the package sun-java6-sdk and apt-get gave me the message:

Package sun-java6-jdk is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jdk has no installation candidate

What I did to solve this problem was to add a new source

sudo add-apt-repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner"
After that a normal

sudo apt-get update
sudo apt-get install sun-java6-jdk
it worked for me.

---

### Post by jcolyn on 2010-08-22
To get sun-java6 you have to enter at the terminal ```
sudo apt-get install sun-java6-jre sun-java6-bin sun-java6-plugin
```

During the install you will have to agree to the EUL..

---

### Post by aryanwicked on 2010-09-04
**After proprietary Sun JRE installation, Is it mandatory to remove OpenJDK or not?** Any conflict?

---

### Post by howefield on 2010-09-04
> **aryanwicked said:**
> After proprietary Sun JRE installation, Is it mandatory to remove OpenJDK or not?

No it is not mandatory, both should co-exist quite peacefully.

---

### Post by scouser73 on 2010-09-04
Here's a site I use to help me install the latest version Of Java from Sun Microsystems: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

