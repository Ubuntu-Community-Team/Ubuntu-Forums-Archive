---
title: "Namoroka Java Web Start Help"
date: 2010-02-10
forum: General Help
---

### Post by gavinlew on 2010-02-10
Hi All,

I have a problem with namoroka and java web start.

I have WINE installed and JVM , which is used to run a windows program, however, Namoroka has associated itself with the Wine JVM when a Java web start file is launched.

This is causing the Java Web Start app to fail.

How can I change the association within Namoroka back to use JWS at /usr/lib/jvm/java-6-sun/jre/javaws , the association doesnt appear within Namoroka's preferences.

Or how can I remove Namoroka completely from my machine and roll back to Firefox 3.5 ?

Cheers,

---

### Post by lovinglinux on 2010-02-10
See how to install java for Namoroka at [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

If you want to remove Namoroka, please specify how you installed it. Did you use a PPA, Ubuntuzilla or simply extracted the tar file from Mozilla?

---

### Post by gavinlew on 2010-02-10
Hi,

The problem I have is with the Namoroka helper/extension/association , calling the windows version.

I have installed the java plugin, however the application i run uses java web start.

It would appear Namoroka is calling the WINE version, as Java bombs out with a Windows orientated error.

Namoroka is also installed from a PPA on my machine.

---

### Post by lovinglinux on 2010-02-10
> **gavinlew said:**
> Hi,

The problem I have is with the Namoroka helper/extension/association , calling the windows version.

I have installed the java plugin, however the application i run uses java web start.

It would appear Namoroka is calling the WINE version, as Java bombs out with a Windows orientated error.

Namoroka is also installed from a PPA on my machine.


If you have a plugin issue, then close Firefox, go to your Firefox profile folder, under ~/.mozilla/firefox and delete the file *pluginreg.dat*. If you have a problem with which application is launched when you click a link, then delete the file *mimeTypes.rdf* (this will reset all application options).

---

### Post by afrodeity on 2010-04-18
bump

---

### Post by afrodeity on 2010-04-18
I have Namaroka installed. Do I need to install java as above? How to test if my java is working properly?

---

### Post by afrodeity on 2010-04-25
> **lovinglinux said:**
> See how to install java for Namoroka at [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

If you want to remove Namoroka, please specify how you installed it. Did you use a PPA, Ubuntuzilla or simply extracted the tar file from Mozilla?

Manually installing the JRE as per the instuctions at linuxtipsproject worked for me. Not sure if my browser is slower now, but it is registering as having java.:P

---

### Post by afrodeity on 2010-04-25
Offloading java to the GPU would really help

[http://news.softpedia.com/news/Utilizing-the-GPU-to-Handle-JavaScript-Code-133134.shtml](http://news.softpedia.com/news/Utilizing-the-GPU-to-Handle-JavaScript-Code-133134.shtml)

---

