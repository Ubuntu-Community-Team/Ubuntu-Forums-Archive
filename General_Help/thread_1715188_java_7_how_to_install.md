---
title: "java 7 how to install"
date: 2011-03-26
forum: General Help
---

### Post by zaabs on 2011-03-26
Heard java 7 gives minecraft a speed boost

---

### Post by 5149.5 on 2011-03-26
You'll have to do the manual installation or use alien to convert the rpm.

[http://www.java.com/en/download/help/linux_install.xml#selfextracting](http://www.java.com/en/download/help/linux_install.xml#selfextracting)

---

### Post by Spyderkid on 2011-03-26
Do not download from site! It caused me to have to do a hard reset for un-known reasons ....

---

### Post by fuzetsu490 on 2011-04-02
check [this thread out]("http://www.minecraftforum.net/viewtopic.php?f=3&t=243959#p3458930") I managed to get it working with this, just extract the tar.gz file to a folder and change this guys script according to your folders. If you're running 64-bit you would have to change the i386 part too. 

```
LD_LIBRARY_PATH=/usr/lib/jvm/jdk1.7.0/jre/lib/i386
export LD_LIBRARY_PATH
padsp java -Djava.library.path=/usr/lib/jvm/jdk1.7.0/jre/lib/i386 -jar /home/nick/jars/Minecraft.jar
```

Also ^ the part that says 'java -Djava....' up there the java in that part would have to be replaced with the java file in the bin folder (of the folder you extracted) in my case the script looks like this.

```
#! /bin/bash
LD_LIBRARY_PATH=/home/USERNAME/Desktop/jre1.7.0/lib/amd64
export LD_LIBRARY_PATH
padsp /home/USERNAME/Desktop/jre1.7.0/bin/java -Djava.library.path=/home/USERNAME/Desktop/jre1.7.0/lib/amd64 -Xmx1324M -Xms1324M -jar /home/USERNAME/Documents/minecraft.jar
```

Hopefully this isn't too hard to understand, I'm not too good at explaining these kinds of things.

---

