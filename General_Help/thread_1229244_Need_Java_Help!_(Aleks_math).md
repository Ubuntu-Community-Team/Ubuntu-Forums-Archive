---
title: "Need Java Help! (Aleks math)"
date: 2009-08-01
forum: General Help
---

### Post by Nick43092 on 2009-08-01
[SIZE=2]A friend of mine got a laptop recently, a Dell Inspiron 15b, with Ubuntu 8.10, i586 architecture. She does Aleks math through school, and cannot get the plugin to work. She has tried putting in:
[/SIZE][SIZE=2]sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/ext/aleksPack10.jar

That's the best I was able to figure out from this site, but the topics were a year and two old, and well, she loads Aleks up, and it still doesn't respond, presumably the plugin isn't working. Any ideas what might be the cause? Could an old version of Java help? 

I've had Ubuntu myself for less than a year, so I not being too verbose in responses would be ultra-appreciated.
[/SIZE]

---

### Post by michy99 on 2009-08-01
I think the command should be:```
sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.10/jre/lib/ext/
```

Check next post instead!!

---

### Post by michy99 on 2009-08-01
Actually, she needs to check which version of Java she has mine is java-6-sun-1.6.0.14 so the command would be```
sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0.14/jre/lib/ext/
```To see which she has use```
ls /usr/lib/jvm
```

---

### Post by Nick43092 on 2009-08-01
[SIZE=2]Thanks for the ideas, but I had her check the Java version, it's definitely [/SIZE][SIZE=2]java-6-sun-1.6.0.10

I tried it with and without the filename on the end. I assume this is important? 
[/SIZE]

---

### Post by QIII on 2009-08-02
Make sure you have Mulitverse in Software Sources.  The repositories have Update 14.

In the terminal:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-jdk
```

You can leave out the jdk if you want.

To make sure that Sun's Jave is preferred over OpenJDK if you have it:

```
sudo update-java-alternatives -s java-6-sun
```

Then check your version:

```
java -version
```

---

### Post by blagosphere on 2010-05-29
> **QIII said:**
> Make sure you have Mulitverse in Software Sources.  The repositories have Update 14.

In the terminal:

```
sudo apt-get install sun-java6-jre sun-java6-plugin sun-java6-bin sun-java6-jdk
```You can leave out the jdk if you want.

To make sure that Sun's Jave is preferred over OpenJDK if you have it:

```
sudo update-java-alternatives -s java-6-sun
```Then check your version:

```
java -version
```



when i do the above i get a "E: package sun-java6-jre has no installation candidate."
[running lucid]
  as per the original post if you go to "www.aleks.com/plugin" it saves the plugin to the browser cache so there is no installation of the aleks plugin.

---

### Post by ronr255 on 2011-03-08
I have it working pretty good in 10.10.  Every once in awhile, you can't put text into the answer box, but if you hit next, then it functions correctly again.  It doesn't happen often, but it does happen.

I went to the package manager and installed sun-java6-jre, plugin, bin, and jdk.  I put typed sudo update-java-alternatives -s java-6-sun in a terminal window, then I typed sudo cp **directory of jarfile here** usr/lib/jvm/java-1.6.0.24/jre/lib/ext.

I rebooted and did some firefox updates and refreshes on the aleks page, and it kind of works...

---

### Post by KaalaTzvya on 2011-03-18
I'm a one-week old Ubuntu user and am so thankful for the above posts, which have gotten me part of the way to setting up Aleks for my son.  After entering this command:

sudo cp aleksPack10.jar /usr/lib/jvm/java-6-sun-1.6.0_24/jre/lib/ext/

I get the following response:

cp: cannot stat `aleksPack10.jar': No such file or directory

I'm not sure how to proceed.  Any help is greatly appreciated.

---

