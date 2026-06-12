---
title: "Can't get Java plugin to work in Firefox"
date: 2010-03-24
forum: General Help
---

### Post by zooounds on 2010-03-24
I have tried everything according to the instructions.

My packages:

```

$ dpkg -l | grep java6
ii  sun-java6-bin                              6-15-1                                                     Sun Java(TM) Runtime Environment (JRE) 6 (architecture depend
ii  sun-java6-fonts                            6-15-1                                                     Lucida TrueType fonts (from the Sun JRE)
ii  sun-java6-jre                              6-15-1                                                     Sun Java(TM) Runtime Environment (JRE) 6 (architecture indepe
ii  sun-java6-plugin                           6-15-1                                                     The Java(TM) Plug-in, Java SE 6

```

Firefox says:

```

Java(TM) Plug-in 1.6.0_15-b03

    Filnamn: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_15

MIME-typ 	Beskrivning 	Filändelse 	Aktiverad
application/x-java-vm 	Java™ Plug-in 		Ja
application/x-java-applet 	Java™ Plug-in Applet 		Ja
application/x-java-applet;version=1.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.1.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.1.2 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.1.3 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.2 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.2.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.2.2 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.3 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.3.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.4 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.4.1 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.4.2 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.5 	Java™ Plug-in 		Ja
application/x-java-applet;version=1.6 	Java™ Plug-in 		Ja
application/x-java-applet;jpi-version=1.6.0_15 	Java™ Plug-in 		Ja
application/x-java-bean 	Java™ Plug-in JavaBeans 		Ja
application/x-java-bean;version=1.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.1.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.1.2 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.1.3 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.2 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.2.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.2.2 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.3 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.3.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.4 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.4.1 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.4.2 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.5 	Java™ Plug-in 		Ja
application/x-java-bean;version=1.6 	Java™ Plug-in 		Ja
application/x-java-bean;jpi-version=1.6.0_15 	Java™ Plug-in

```

("Ja" means "Yes")

But java.com:s test page can't detect my java.

---

### Post by wojox on 2010-03-24
Followed this guide here and got it running good: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by zooounds on 2010-03-24
> **wojox said:**
> Followed this guide here and got it running good: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I have, but it still uses the deb-installed older version of java. I can't uninstall it at it would remove lots of other stuff, like open office.

Firefox says:


```
Java(TM) Plug-in 1.6.0_15-b03

    Filnamn: libjavaplugin_oji.so
    Java(TM) Plug-in 1.6.0_15
```


In the terminal:


```
$ java -version
java version "1.6.0_18"
Java(TM) SE Runtime Environment (build 1.6.0_18-b07)
Java HotSpot(TM) Server VM (build 16.0-b13, mixed mode)

```

---

### Post by zooounds on 2010-03-24
Where does Firefox search for plugins? it seems like it find an older version of the plugin instead of the one I just installed.

---

### Post by zooounds on 2010-03-24
Now I have removed the other java too so all that is left is my newly installed version.

Firefox still uses the older plugin which I can't find anywhere.

---

### Post by wojox on 2010-03-24
And you ran these two commands:

```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_18/bin/java" 1
```

```
sudo update-alternatives --set java /opt/java/32/jre1.6.0_18/bin/java
```

---

### Post by wojox on 2010-03-24
Which version of Firefox?

---

### Post by zooounds on 2010-03-24
> **wojox said:**
> And you ran these two commands:

```
sudo update-alternatives --install "/usr/bin/java" "java" "/opt/java/32/jre1.6.0_18/bin/java" 1
```

```
sudo update-alternatives --set java /opt/java/32/jre1.6.0_18/bin/java
```

of course:

```

$ sudo update-alternatives --config  java 
Det finns 1 val för alternativet java (som tillhandahåller /usr/bin/java).

  Val          Sökväg                           Prioritet  Status
------------------------------------------------------------
  0            /opt/java/32/jre1.6.0_18/bin/java   1         automatiskt läge
* 1            /opt/java/32/jre1.6.0_18/bin/java   1         manuellt läge


```

Firefox is 3.5.8

---

### Post by wojox on 2010-03-24
And then: 

```
mkdir ~/.mozilla/plugins
```

```
ln -s /opt/java/32/jre1.6.0_18/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/
```

Close your browser and go to [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

---

### Post by zooounds on 2010-03-24
> **wojox said:**
> And then: 

```
mkdir ~/.mozilla/plugins
```

```
ln -s /opt/java/32/jre1.6.0_18/plugin/i386/ns7/libjavaplugin_oji.so ~/.mozilla/plugins/
```

Close your browser and go to [http://java.com/en/download/installed.jsp](http://java.com/en/download/installed.jsp)

Already done that. it doesn't work.

I have also search the entire disk for files named "libjavaplugin_oji.so". The only one is the one I have installed.

---

### Post by zooounds on 2010-03-24
Alson, removing the .mozilla directory to create a new profile gives the same error, wrong version of plugin.

---

### Post by zooounds on 2010-03-24
I installed Firefox 3.6 and changed the symlinks as described in the guide. Got no java plugin at all.

Reinstalled 3.5 and adjusted the links again. Now it won't see the plugin at all.

---

### Post by donsy on 2010-03-24
[QUOTE=zooounds;9021705]I have tried everything according to the instructions.

My packages:

```

$ dpkg -l | grep java6
ii  sun-java6-bin                              6-15-1                                                     Sun Java(TM) Runtime Environment (JRE) 6 (architecture depend
ii  sun-java6-fonts                            6-15-1                                                     Lucida TrueType fonts (from the Sun JRE)
ii  sun-java6-jre                              6-15-1                                                     Sun Java(TM) Runtime Environment (JRE) 6 (architecture indepe
ii  sun-java6-plugin                           6-15-1                                                     The Java(TM) Plug-in, Java SE 6

```

Remove all the sun-java6-* packages AND java-common. Then in Firefox click on a Web page that uses Java, and at the prompt for additional plug-ins needed choose the Java plug-in (second option).

---

### Post by Ancanus on 2010-03-24
Have you considered trying openjdk-6 ?

---

### Post by sgosnell on 2010-03-24
Try this: ```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by zooounds on 2010-03-25
> **sgosnell said:**
> Try this: ```
sudo apt-get install ubuntu-restricted-extras
```

Already done.

---

### Post by pourquoipas on 2010-03-25
u have firefox 3.6 and java 6 from sun try with 
[COLOR=#000000]sudo ln -s  /usr/lib/jvm/java-6-sun/jre/lib/i386/libnpjp2.so  /usr/lib/firefox-3.6/plugins[/COLOR]
worked for me, 
found the solution here [http://ubuntuforums.org/showthread.php?t=1425311&page=2](http://ubuntuforums.org/showthread.php?t=1425311&page=2)

---

### Post by sgosnell on 2010-03-25
Dunno, then.  All I had to do was install the restricted extras and reboot.  The java plugin started working immediately.  I had previously installed the jre, which didn't help, but I did nothing else that I can remember.

---

