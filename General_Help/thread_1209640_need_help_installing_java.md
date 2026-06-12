---
title: "need help installing java"
date: 2009-07-10
forum: General Help
---

### Post by bodyofchrist on 2009-07-10
i downloaded the linux java today and am trying to get it installed from what i read, i have to use terminal to install the .bin file.
well i go to terminal
su
then it asks me for a password and i give the password i sign into everything with and i get an authentification error

---

### Post by Regenweald on 2009-07-10
rather that that, go to System>>administration>>Synaptic Package Manager and search for java. Then check the java-common package for installation.

---

### Post by credobyte on 2009-07-10
```
sudo apt-get install sun-java6-jre sun-java6-plugin

```
[COLOR=Gray]sun-java6-jdk[/COLOR] and [COLOR=Gray]sun-java6-fonts[/COLOR] if you need JDK.

---

### Post by bodyofchrist on 2009-07-10
alright i clicked reinstall. do i need to restart?

---

### Post by rocket16 on 2009-07-10
Hello friend. Actually, you can install Java from Terminal as well as Synaptic, but I've done it from Add/Remove Programmes. To access it, simply go to Applications->Add/Remove Programmes. And, make sure to check the teb to "All Available Applications". Now, go to the search box, and Type Java. Then, you will get two or three applications, and select your choice. Now, allow the Java Virtual Machine to get installed automatically using he Internet. After the installation is completed, your Java VM is ready. Now, you can use Java from Terminal. For example, if you have a java file named q.java on your home directory, open a Terminal window there, and type exactly: "java q" (without the quotes). If you want a development platform for Java, you need to have the Eclipse AEnvironment, which you can install from Applications->Add/Remove Programmes, by searching for eclipse and installing it by the same process.

---

### Post by bodyofchrist on 2009-07-10
so i have java 6 downloaded but it still says im using 1.6.0_0.

also, what do i need to make media players like imeem and the myspace music player work?

---

