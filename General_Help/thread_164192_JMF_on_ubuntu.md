---
title: "JMF on ubuntu"
date: 2006-04-22
forum: General Help
---

### Post by salvo1 on 2006-04-22
I installed sun-j2sdk1.5 using automatix/synaptic (i don't remember) and all works fine... Now i want (I need!) to build an mp3 player in JAVA and i need to install JMF.

1. Nothing in Synaptic
2. I download JMF from [here](http://java.sun.com/products/java-media/jmf/2.1.1/download.html). 
3. I download the plugin for mp3 from [here](http://"http://java.sun.com/products/java-media/jmf/mp3/download.html")
4. I read [this guide](http://java.sun.com/products/java-media/jmf/2.1.1/setup-linux.html).

```

$ chmod +x jmf-2_1_1e-linux.bin
$ ./jmf-2_1_1e-linux.bin
[...]
Unpacking...
Extracting...
UnZipSFX 5.40 of 28 November 1998, by Info-ZIP (Zip-Bugs@lists.wku.edu).
   creating: JMF-2.1.1e/
[...]
Done.

$ setenv JMFHOME /home/salvo/Desktop/JMF-2.1.1e
bash: setenv: command not found

```

5. I read [this](http://www.ubuntuforums.org/showthread.php?t=107510&highlight=JMF), [this](http://www.ubuntuforums.org/showthread.php?t=103990&highlight=JMF) and [this](http://www.ubuntuforums.org/showthread.php?t=67823&highlight=JMF).

```

salvo@toshiba:~/Desktop$ export JMFHOME=/home/salvo/Desktop/JMF-2.1.1e
salvo@toshiba:~/Desktop$ export CLASSPATH=$JMFHOME/lib/jmf.jar:.:$CLASSPATH
salvo@toshiba:~/Desktop$ export LD_LIBRARY_PATH=$JMFHOME/lib:$LD_LIBRARY_PATH

```

6. [This site](http://java.sun.com/products/java-media/jmf/2.1.1/jmfdiagnostics.html) answer me:

```
JMF Diagnostics:

Java 1.1 compliant browser.....Maybe
JMF classes.....Not Found
```

----

Concerning the mp3 plugin...

7. I read the guide

[quote="http://java.sun.com/products/java-media/jmf/mp3/download.html"]For the plugin to work within a JMF application, you need to :
- ensure that jmf.jar is also in the /lib/ext directory
- run the following command:
java com.sun.media.codec.audio.mp3.JavaDecoder
[/quote]

8. So that, I copy the .jar file in /home/salvo/Desktop/JMF-2.1.1e/lib
9. I copy the .jar file in /usr/lib/j2sdk1.5-sun/jre/lib/ext

Nothing going right.. What's the matter?

---

### Post by oberoc on 2006-04-22
What is the mp3 package that you trying to install? And where does com.sun.media.codec.udio.mp3.JavaDecodeer live?

---

### Post by salvo1 on 2006-04-22
[QUOTE=oberoc]What is the mp3 package that you trying to install? And where does com.sun.media.codec.udio.mp3.JavaDecodeer live?[/QUOTE]

"[MP3 support for JMF]("http://java.sun.com/products/java-media/jmf/mp3/download.html") We are excited to announce MP3 support for JMF! Please proceed to the download page to get your hands on this highly anticipated addition to JMF."

---

