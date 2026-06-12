---
title: "Problem Azureus 2.4.0.4 and Java 1.5!"
date: 2006-06-04
forum: General Help
---

### Post by vumba on 2006-06-04
I have install azureus with this wizard : [here]("http://www.ubuntuforums.org/showthread.php?t=144546&highlight=azureus")

I have install Java 1.5 with repositories 

repositories from : [here]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_add_extra_repositories") 

and i have install java: [here]("http://easylinux.info/wiki/Ubuntu_dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox")

My Java version is :

:~$ java -version
java version "1.5.0_06"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.5.0_06-b05)
Java HotSpot(TM) Client VM (build 1.5.0_06-b05, mixed mode, sharing)

and i have clicked it with command :

sudo update-alternatives --config java


There are 3 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
        1        /usr/bin/gij-wrapper-4.1
 +    2        /usr/lib/jvm/java-gcj/jre/bin/java
*     3        /usr/lib/jvm/java-1.5.0-sun/jre/bin/java

Press enter to keep the default[*], or type selection number:


This image which is in the site : [here]("http://www.ubuntuforums.org/showthread.php?t=144546&page=3&highlight=azureus")

When this image is on the screen and i press hide and it don't go away.

Please help me ... ](*,)

---

### Post by dubz13 on 2006-06-05
I have the same problem as do many other people I believe...  It looks like the best fix right now for that specific popup is to close Azureus properly (File>Exit on the azureus window) and then rerun it.

---

### Post by beuno on 2006-06-05
I updated to Azureus latest version (CVS) and all those UI problems got fixed.

1. Download: [http://torrents.aelitis.com:88/files/Azureus2403-B35.jar](http://torrents.aelitis.com:88/files/Azureus2403-B35.jar)
2. Fire up a terminal
3. Close Azureus
4. Execute: sudo mv /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar.old
5. Execute: sudo mv /home/YOUR_USER_NAME/Desktop/Azureus2403-B35.jar /usr/share/java/Azureus2.jar

(basically overwrite Azureus2.jar with this one)

Fire up Azureus again and it's fixed

I blogged about it in spanish over at: [http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/](http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/)

---

### Post by dubz13 on 2006-06-05
Nice. Hopefully once the stable is released the azureus synaptic package will work properly aswell.

---

### Post by dudus on 2006-06-05
It's an azureus bug. Confirm this in malone:

[https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813](https://launchpad.net/distros/ubuntu/+source/azureus/+bug/41813)

---

### Post by vumba on 2006-06-05
[QUOTE=beuno]I updated to Azureus latest version (CVS) and all those UI problems got fixed.

1. Download: [http://torrents.aelitis.com:88/files/Azureus2403-B35.jar](http://torrents.aelitis.com:88/files/Azureus2403-B35.jar)
2. Fire up a terminal
3. Close Azureus
4. Execute: sudo mv /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar.old
5. Execute: sudo mv /home/YOUR_USER_NAME/Desktop/Azureus2403-B35.jar /usr/share/java/Azureus2.jar

(basically overwrite Azureus2.jar with this one)

Fire up Azureus again and it's fixed

I blogged about it in spanish over at: [http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/](http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/)[/QUOTE]

I don't understand this process!
and i don't have this sudo mv /usr/share/java/"Azureus2.jar" document! why?

---

### Post by beuno on 2006-06-05
[QUOTE=vumba]I don't understand this process!
and i don't have this sudo mv /usr/share/java/"Azureus2.jar" document! why?[/QUOTE]

All I'm doing is replacing Azureus2.jar, so I'm renaming the old one so you can keep a backup just in case, and then moving the new one to the location the old file was.

---

### Post by kairu0 on 2006-06-10
[QUOTE=beuno]I updated to Azureus latest version (CVS) and all those UI problems got fixed.

1. Download: [http://torrents.aelitis.com:88/files/Azureus2403-B35.jar](http://torrents.aelitis.com:88/files/Azureus2403-B35.jar)
2. Fire up a terminal
3. Close Azureus
4. Execute: sudo mv /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar.old
5. Execute: sudo mv /home/YOUR_USER_NAME/Desktop/Azureus2403-B35.jar /usr/share/java/Azureus2.jar

(basically overwrite Azureus2.jar with this one)

Fire up Azureus again and it's fixed

I blogged about it in spanish over at: [http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/](http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/)[/QUOTE]

Worked for me!

---

### Post by Orixyu on 2006-06-10
Should I update Azuerus once I have patched the problem with these steps?

---

### Post by ctucker10 on 2006-06-10
[QUOTE=beuno]I updated to Azureus latest version (CVS) and all those UI problems got fixed.

1. Download: [http://torrents.aelitis.com:88/files/Azureus2403-B35.jar](http://torrents.aelitis.com:88/files/Azureus2403-B35.jar)
2. Fire up a terminal
3. Close Azureus
4. Execute: sudo mv /usr/share/java/Azureus2.jar /usr/share/java/Azureus2.jar.old
5. Execute: sudo mv /home/YOUR_USER_NAME/Desktop/Azureus2403-B35.jar /usr/share/java/Azureus2.jar

(basically overwrite Azureus2.jar with this one)

Fire up Azureus again and it's fixed

I blogged about it in spanish over at: [http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/](http://www.kbglob.com/gnulinux/ubuntu/azureus-usable-en-ubuntu-dapper/)[/QUOTE]

Thanks. It works like a charm!

---

