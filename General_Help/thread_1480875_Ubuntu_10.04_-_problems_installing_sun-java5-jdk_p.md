---
title: "Ubuntu 10.04 - problems installing sun-java5-jdk properly"
date: 2010-05-12
forum: General Help
---

### Post by Performer24 on 2010-05-12
This may be silly problem but since I am first time Ubuntu/Debian user I would like to ask for help.

I have tried to properly install sun-java5-jdk to prepare android build environment on dedicated virtual machine with Ubuntu 10.04 desktop x86 installation. The problem is that packages are not available in canonical repositories for lucid and install from sun packages does not work properly - i.e. for rpm there is a lot of missing dependencies and bin package just extracts directory tree without proper installation.

I know that sun java is deprectaed and we should use OpenJDK but even there are only repositories for JDK version 6 which is unsupported by android build environment.

Synaptic Package Manager command Force Version on JDK6  is inactive (for both open and sun) and I can not find any JDK  5 available for install.

Any ideas for easy workaround.

---

### Post by Performer24 on 2010-05-12
Added to repositories paths to jaunty distribution - that gives an access to all java 5 packages

---

### Post by zer0her0 on 2010-06-14
Thanks, I'd be trying to find the easiest way of doing this and your follow up was perfect thank you.

---

### Post by joe4227 on 2010-10-27
Yeah, yeah, I know - deprecated.

But many books on SOA and JAVA right now still use Java-5.

I need to install correctly so I can use update-java-alternatives to switch between 5 & 6.

Could someone please add the Ubuntu sun-java5-jdk back to the repository??

---

### Post by nasa2011 on 2011-01-11
I am not able to ap-get sun-java5-jdk from ubuntu10.10 64bit OS. Any pointers.... ?

---

### Post by larka06 on 2011-01-14
Ubuntu/Debian does not use rpm's.

---

### Post by irfans on 2011-02-16
> **Performer24 said:**
> Added to repositories paths to jaunty distribution - that gives an access to all java 5 packages
Please tell me as to what exactly needs to be added and where?
I am using the Lucid distribution

---

