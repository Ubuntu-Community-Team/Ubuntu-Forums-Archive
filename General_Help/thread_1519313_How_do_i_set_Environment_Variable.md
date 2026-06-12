---
title: "How do i set Environment Variable?"
date: 2010-06-28
forum: General Help
---

### Post by Simdog1 on 2010-06-28
Well on a Rsps forum it says that the reason i keep crashing in the client is cause my Envieronment Variable isnt set for Java. i was wondering how to do this. 

please make it deatailed since i am new to ubuntu and i dont know most of the things like usr/java
thanks

---

### Post by lukeiamyourfather on 2010-06-28
Ubuntu uses bash.

[http://www.mcsr.olemiss.edu/unixhelp/environment/env3d.html](http://www.mcsr.olemiss.edu/unixhelp/environment/env3d.html)

The link says use ~./bash_profile, but its ~/.bashrc in Ubuntu if I remember correctly. Not on Ubuntu currently so I can't check. Cheers!

---

### Post by Simdog1 on 2010-07-10
im new with this command things how would i use it for Java?

---

### Post by BenB1 on 2010-07-10
Look in your home directory for a file named .bashrc. You can edit this without being root. In fact it's probably better to not be root to edit it. In the file you put the following:

# Export / Set the Java home path.
export JAVA_HOME=/usr/java/jdk1.5.0_07/bin/java

# Export / Set path.
export PATH=$PATH:/usr/java/jdk1.5.0_07/bin

You'll need to know which java you've installed, and its location. The ones in the examples above are just examples. /usr/share/java  might be where yours is located. It is where mine is stashed away.

Save the file, exit out of the editor. Your environment should now be set. 

You might also consider [reading]("http://www.cyberciti.biz/faq/linux-unix-set-java_home-path-variable/") a little. And of course, dear old [Google]("http://www.google.com/search?hl=en&source=hp&q=Setting+bash+variables+for+java&aq=f&aqi=g1&aql=&oq=&gs_rfai=CLw1hnCc5TMz8FJX6gAS684TmBwAAAKoEBU_QLBFB") links out to more reading, in case I've not provided adequate help.

---

### Post by Simdog1 on 2010-07-12
umm this might sound stupid but whats a home directory and where can i find .bashrc. and for the #export do i make a new thing or open the bash and put it in it

---

### Post by Simdog1 on 2010-07-14
Bump. please help

---

### Post by lisati on 2010-07-14
> **Simdog1 said:**
> umm this might sound stupid but whats a home directory and where can i find .bashrc. and for the #export do i make a new thing or open the bash and put it in it

A "home" directory is a folder where a user's files are stored. Each user on your system will have their own separate folder. Have a look at the "places" menu - there should be an entry "Home folder" (or similar)

Because  ".bashrc" begins with a dot, it might be hidden when you open your home folder. If you're using the graphical display (i.e. not using a command line) you can use view->show hidden files.

---

### Post by Simdog1 on 2010-07-14
so wpuld mine be like File System/Home/family/Desktop?

---

### Post by Simdog1 on 2010-07-18
^^^^^^^

---

### Post by AlphaLexman on 2010-07-18
YOUR home directory is:
```
/home/simdog1/
```
if simdog1 is your username on your machine.

There is no text or spaces before the very first '/'

You can get there in a terminal by the following:
```
cd /home/simdog1/
```
(replace 'simdog1' with your actual username if different)
or,
```
cd ~
```
will do the same thing regardless if 'simdog1' or 'simdog2' is your actual username.

---

### Post by lkjoel on 2010-07-18
> **Simdog1 said:**
> so wpuld mine be like File System/Home/family/Desktop?
So you are familiar with the menu right?
Open up the Applications menu, and you will see Accessories.
On Accessories, click on Terminal Emulator (Or Terminal).
On that, type this code in:
```
gedit ~/.bashrc
```
A window will pop up, and you can enter those lines in.
If you want to see what is your home directory, type this code in the Terminal:
```
echo ~
```
That is where your home directory is.

---

### Post by Simdog1 on 2010-07-20
o and how can i find where my javai s downloaded? or download it cause i cant find it but i see my /usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java but cant find my jdk to set my export path or export java_home

---

### Post by Simdog1 on 2010-07-29
bump

---

### Post by lkjoel on 2010-07-31
> **Simdog1 said:**
> o and how can i find where my javai s downloaded? or download it cause i cant find it but i see my /usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java but cant find my jdk to set my export path or export java_home
First of all, update java to the newest version.
```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
```
Then could you show me the results of this for me?
```
find / | grep "java"
```

---

### Post by Simdog1 on 2010-08-01
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Algiers
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Casablanca
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Maputo
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Djibouti
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Asmara
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Kinshasa
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Harare
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Addis_Ababa
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Porto-Novo
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Johannesburg
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Dar_es_Salaam
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Ndjamena
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Sao_Tome
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Gaborone
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Bissau
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Tunis
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Nairobi
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Kigali
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Ouagadougou
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Banjul
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Bujumbura
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Blantyre
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Bamako
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Douala
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Africa/Mogadishu
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/EET
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Tirane
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Copenhagen
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Athens
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Monaco
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Vaduz
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Brussels
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Samara
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Istanbul
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Minsk
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Stockholm
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Prague
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Vilnius
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Helsinki
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Malta
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Moscow
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Madrid
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Riga
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Warsaw
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Zaporozhye
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Kiev
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Bucharest
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Sofia
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Vienna
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Belgrade
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Berlin
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Budapest
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Chisinau
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Rome
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Amsterdam
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Paris
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Zurich
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Uzhgorod
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Dublin
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Luxembourg
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Oslo
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Lisbon
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/London
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Kaliningrad
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Gibraltar
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Volgograd
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Simferopol
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Andorra
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Europe/Tallinn
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/GMT
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Darwin
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Currie
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Lord_Howe
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Lindeman
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Eucla
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Adelaide
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Melbourne
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Hobart
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Broken_Hill
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Sydney
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Brisbane
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/Australia/Perth
/usr/lib/jvm/java-6-openjdk/jre/lib/zi/PST8PDT
/usr/lib/jvm/java-6-openjdk/jre/lib/accessibility.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/charsets.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/cmm
/usr/lib/jvm/java-6-openjdk/jre/lib/cmm/sRGB.pf
/usr/lib/jvm/java-6-openjdk/jre/lib/cmm/PYCC.pf
/usr/lib/jvm/java-6-openjdk/jre/lib/cmm/CIEXYZ.pf
/usr/lib/jvm/java-6-openjdk/jre/lib/cmm/GRAY.pf
/usr/lib/jvm/java-6-openjdk/jre/lib/cmm/LINEAR_RGB.pf
/usr/lib/jvm/java-6-openjdk/jre/lib/about.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/meta-index
/usr/lib/jvm/java-6-openjdk/jre/lib/about.jnlp
/usr/lib/jvm/java-6-openjdk/jre/lib/management-agent.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/management
/usr/lib/jvm/java-6-openjdk/jre/lib/management/snmp.acl
/usr/lib/jvm/java-6-openjdk/jre/lib/management/jmxremote.access
/usr/lib/jvm/java-6-openjdk/jre/lib/management/jmxremote.password
/usr/lib/jvm/java-6-openjdk/jre/lib/management/management.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/im
/usr/lib/jvm/java-6-openjdk/jre/lib/im/indicim.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/im/thaiim.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/jce.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/compilefontconfig.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/content-types.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/calendars.properties
/usr/lib/jvm/java-6-openjdk/jre/lib/rt.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/jsse.jar
/usr/lib/jvm/java-6-openjdk/jre/lib/currency.data
/usr/lib/jvm/java-6-openjdk/jre/lib/fontconfig.properties
/usr/lib/jvm/java-6-openjdk/docs
/usr/lib/jvm/java-6-openjdk/bin
/usr/lib/jvm/java-6-openjdk/bin/unpack200
/usr/lib/jvm/java-6-openjdk/bin/rmiregistry
/usr/lib/jvm/java-6-openjdk/bin/java
/usr/lib/jvm/java-6-openjdk/bin/java-rmi.cgi
/usr/lib/jvm/java-6-openjdk/bin/javaws
/usr/lib/jvm/java-6-openjdk/bin/servertool
/usr/lib/jvm/java-6-openjdk/bin/tnameserv
/usr/lib/jvm/java-6-openjdk/bin/rmid
/usr/lib/jvm/java-6-openjdk/bin/pack200
/usr/lib/jvm/java-6-openjdk/bin/keytool
/usr/lib/jvm/java-6-openjdk/bin/orbd
/usr/lib/jvm/java-6-openjdk/bin/policytool
/usr/lib/jvm/java-6-openjdk/bin/pluginappletviewer
/usr/lib/jvm/java-6-openjdk/man
/usr/lib/jvm/java-6-openjdk/man/ja
/usr/lib/ure/share/java
/usr/lib/ure/share/java/ridl.jar
/usr/lib/ure/share/java/juh.jar
/usr/lib/ure/share/java/java_uno.jar
/usr/lib/ure/share/java/unoloader.jar
/usr/lib/ure/share/java/jurt.jar
/usr/lib/ure/share/misc/javavendors.xml
/usr/lib/ure/bin/javaldx
/usr/lib/ure/lib/javaloader.uno.so
/usr/lib/ure/lib/libjava_uno.so
/usr/lib/ure/lib/javavm.uno.so
/usr/lib/ure/lib/sunjavaplugin.so
/usr/lib/ure/lib/libjava_uno
/usr/lib/mozilla/plugins/libjavaplugin.so
/usr/lib/mime/packages/sun-java6-bin
/usr/lib/python2.6/dist-packages/serial/serialjava.pyc
/usr/lib/python2.6/dist-packages/serial/serialjava.py
/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/tools/Editra/tests/syntax/javascript.js
/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/tools/Editra/tests/syntax/java.java
/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/tools/Editra/src/syntax/java.pyc
/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/tools/Editra/src/syntax/javascript.py
/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/tools/Editra/src/syntax/javascript.pyc
/usr/lib/python2.6/dist-packages/wx-2.8-gtk2-unicode/wx/tools/Editra/src/syntax/java.py
/usr/lib/python2.6/dist-packages/twisted/internet/_javaserialport.py
/usr/lib/python2.6/dist-packages/twisted/internet/_javaserialport.pyc
/home/family/Desktop/508/BatScape Client v3.1/src/Class35.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class43.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub15.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class93.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class105_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub24.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class6.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class45.java
/home/family/Desktop/508/BatScape Client v3.1/src/DataStream.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class48.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub29.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class57.java
/home/family/Desktop/508/BatScape Client v3.1/src/Interface3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub13_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Hack.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class15.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub12.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class4.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class103.java
/home/family/Desktop/508/BatScape Client v3.1/src/ModelLoader.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub3_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub26.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub20.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class113.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class13_Sub3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class35_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub4.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub36.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub18.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub18.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub28.java
/home/family/Desktop/508/BatScape Client v3.1/src/Cache.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub14.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class36.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub28_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub19.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub16.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class72.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class97.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub13.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class78.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub30.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub15.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class28.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class40.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class116.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class83.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub10_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class31.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class49.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class15_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class61.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub23.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub8.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub10.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class55.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub14.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub38.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class14.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub18.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class50_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class69.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class77.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub27.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class26.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class92.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class38.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class110.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class75_Sub3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class35_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub28.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class13_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub11_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class118.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class60.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class98.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub28_Sub4.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub34.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class91.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class23.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class10.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub9.java
/home/family/Desktop/508/BatScape Client v3.1/src/RuntimeException_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub9.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class70.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub11.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub13.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class121.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub21.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub22.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub35.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub4.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class108.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class12.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub17.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class75.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class63.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class47.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class13_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub7.java
/home/family/Desktop/508/BatScape Client v3.1/src/Interface2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class88.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub1_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub11.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub27.java
/home/family/Desktop/508/BatScape Client v3.1/src/CacheManager.java
/home/family/Desktop/508/BatScape Client v3.1/src/Interface1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub11.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub6.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class30.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class107.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class94.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class53.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class8.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class72_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class25.java
/home/family/Desktop/508/BatScape Client v3.1/src/RSString.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class41.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub6.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class106.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class123.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub19.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub8.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class86.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub5.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub28_Sub3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub19.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub23.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class79.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub28_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class124.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class75_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class75_Sub3_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub6.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class90.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub32.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class67.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class81.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub39.java
/home/family/Desktop/508/BatScape Client v3.1/src/Canvas_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class17.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub15.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class39.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class101.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class99.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class120.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class104.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub25.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub7.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class58.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class11.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class50.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub16.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub26_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class9.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class21_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class72_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub7.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub24.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class59.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class62.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class44.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub5.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub5.java
/home/family/Desktop/508/BatScape Client v3.1/src/Loader.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class32.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class95.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class92_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class46.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub8.java
/home/family/Desktop/508/BatScape Client v3.1/src/Interface4.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class66.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class119.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub17.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class76.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub4.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class37.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class42.java
/home/family/Desktop/508/BatScape Client v3.1/src/client.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class96.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class127.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class34.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub9.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class112.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class115.java
/home/family/Desktop/508/BatScape Client v3.1/src/CustomSprites.java
/home/family/Desktop/508/BatScape Client v3.1/src/PacketStream.java
/home/family/Desktop/508/BatScape Client v3.1/src/CacheFileManager.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class65.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub4.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class24.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class73.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class74.java
/home/family/Desktop/508/BatScape Client v3.1/src/Applet_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub37.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class126.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub25.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class54.java
/home/family/Desktop/508/BatScape Client v3.1/src/PacketParser.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub6_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class80.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub10.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class21.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class109.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class71.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class13.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class105.java
/home/family/Desktop/508/BatScape Client v3.1/src/Login.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class87.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class114.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub6.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class52.java
/home/family/Desktop/508/BatScape Client v3.1/src/ItemDef.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class122.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class18.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class75_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class20.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class5.java
/home/family/Desktop/508/BatScape Client v3.1/src/SignLink.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub33.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class50_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub22.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class97_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub10_Sub1_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub16.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class102.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class22.java
/home/family/Desktop/508/BatScape Client v3.1/src/Stream.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class13_Sub4.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub3.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class84.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class27.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class89.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub13_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class33.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub17.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class125.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub5.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub7.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class56.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub26.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class29.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub29.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub2.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20_Sub12.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class85.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class64.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class75_Sub1_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub10.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub12.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class16.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class51.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class71_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub31.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class1_Sub6_Sub1.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class128.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub13_Sub21.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class68_Sub20.java
/home/family/Desktop/508/BatScape Client v3.1/src/Class7.java
/home/family/.icedteaplugin/java.stdout
/home/family/.icedteaplugin/java.stderr
/home/family/.macromedia/Flash_Player/#SharedObjects/4MZ7XMQD/l.yimg.com/a/a/1-/java
/home/family/.macromedia/Flash_Player/#SharedObjects/4MZ7XMQD/l.yimg.com/a/a/1-/java/promotions
/home/family/.macromedia/Flash_Player/#SharedObjects/4MZ7XMQD/l.yimg.com/a/a/1-/java/promotions/pandg
/home/family/.macromedia/Flash_Player/#SharedObjects/4MZ7XMQD/l.yimg.com/a/a/1-/java/promotions/pandg/100728
/home/family/.macromedia/Flash_Player/#SharedObjects/4MZ7XMQD/l.yimg.com/a/a/1-/java/promotions/pandg/100728/a
/home/family/.macromedia/Flash_Player/#SharedObjects/4MZ7XMQD/l.yimg.com/a/a/1-/java/promotions/pandg/100728/a/floatshell.swf
/home/family/.macromedia/Flash_Player/#SharedObjects/4MZ7XMQD/l.yimg.com/a/a/1-/java/promotions/pandg/100728/a/floatshell.swf/lanTest1.sol
/etc/java-6-sun
/etc/java-6-sun/flavormap.properties
/etc/java-6-sun/security
/etc/java-6-sun/security/java.security
/etc/java-6-sun/security/java.policy
/etc/java-6-sun/security/cacerts
/etc/java-6-sun/net.properties
/etc/java-6-sun/sound.properties
/etc/java-6-sun/logging.properties
/etc/java-6-sun/jvm.cfg
/etc/java-6-sun/management
/etc/java-6-sun/management/snmp.acl
/etc/java-6-sun/management/jmxremote.access
/etc/java-6-sun/management/jmxremote.password
/etc/java-6-sun/management/management.properties
/etc/java-6-sun/content-types.properties
/etc/java-6-sun/calendars.properties
/etc/java-6-sun/fontconfig.properties
/etc/.java
/etc/.java/.systemPrefs
/etc/.java/.systemPrefs/.system.lock
/etc/.java/.systemPrefs/.systemRootModFile
/etc/alternatives/javaws.1.gz
/etc/alternatives/java
/etc/alternatives/mozilla-javaplugin.so
/etc/alternatives/xulrunner-1.9-javaplugin.so
/etc/alternatives/javaws
/etc/alternatives/java.1.gz
/etc/alternatives/java_vm
/etc/bash_completion.d/java
/etc/ssl/certs/java
/etc/ssl/certs/java/cacerts
/etc/java-6-openjdk
/etc/java-6-openjdk/flavormap.properties
/etc/java-6-openjdk/security
/etc/java-6-openjdk/security/nss.cfg
/etc/java-6-openjdk/security/java.security
/etc/java-6-openjdk/security/java.policy
/etc/java-6-openjdk/psfont.properties.ja
/etc/java-6-openjdk/psfontj2d.properties
/etc/java-6-openjdk/net.properties
/etc/java-6-openjdk/sound.properties
/etc/java-6-openjdk/images
/etc/java-6-openjdk/images/cursors
/etc/java-6-openjdk/images/cursors/cursors.properties
/etc/java-6-openjdk/fontconfig.bfc
/etc/java-6-openjdk/logging.properties
/etc/java-6-openjdk/swing.properties
/etc/java-6-openjdk/accessibility.properties
/etc/java-6-openjdk/jvm.cfg
/etc/java-6-openjdk/management
/etc/java-6-openjdk/management/snmp.acl
/etc/java-6-openjdk/management/jmxremote.access
/etc/java-6-openjdk/management/jmxremote.password
/etc/java-6-openjdk/management/management.properties
/etc/java-6-openjdk/content-types.properties
/etc/java-6-openjdk/calendars.properties
/etc/java-6-openjdk/fontconfig.properties
/etc/defoma/hints/sun-java6-fonts.hints

umm idk what this meansl ol

---

### Post by Simdog1 on 2010-08-02
i tried doing tutoria from this website 
[http://ubuntuforums.org/showthread.php?t=1360294&highlight=java](http://ubuntuforums.org/showthread.php?t=1360294&highlight=java)
but i get an error saying 
Command 'java' is available in '/usr/bin/java'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
java: command not found
help please

---

### Post by lkjoel on 2010-08-02
*/usr/lib/jvm/java-6-sun-1.6.0.20/jre/bin/java* does not exist.
Use */usr/lib/jvm/java-6-openjdk/bin/java* instead.

---

### Post by Simdog1 on 2010-08-03
crap messed up something somewhere since. yesterday every command i did i always got 
Command 'sudo' is available in '/usr/bin/sudo'
The command could not be located because '/usr/bin' is not included in the PATH environment variable.
sudo: command not found

---

### Post by lkjoel on 2010-08-03
Try using [Terminal Enhancements]("https://launchpad.net/terminal-enhancements").
Then type this in a terminal:
```
gedit ~/.bashrc
```
Then at the end, type:
```
PATH="$PATH:/usr/bin"
```
Then save and exit.
Then type this in a terminal:
```
source ~/.bashrc
```

---

### Post by Simdog1 on 2010-08-04
how do i use it i downloaded install.sh but idk what to do or if i downloaded the right one

---

### Post by btindie on 2010-08-04
Going by [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables) I think you're supposed to use a different file now for environment variables.
 
.pam_environment
 
Open a terminal and type
```
gedit ~/.pam_environment
```
 
Then enter the variable assignments in the form
```
VARIABLE=VALUE
```
i.e.
```
EDITOR=/usr/bin/nano
```
 
Type that in then save it. Close the terminal then start a new one. To see that it's taken affect you can type "echo $EDITOR" in the terminal and it should display "/usr/bin/nano".
 
With your JAVA variables, for it to take affect with the next top you'll need to restart it. If it still works these days with Ubuntu you can do Ctrl+Alt+Backspace, a logout or reboot at the extreame.

---

