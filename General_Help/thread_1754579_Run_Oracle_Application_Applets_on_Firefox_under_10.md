---
title: "Run Oracle Application Applets on Firefox under 10.10"
date: 2011-05-10
forum: General Help
---

### Post by eng.ahmedgaber on 2011-05-10
I want to replace my windows clients with ubuntu clients, i have a problem when run Oracle Application 10g on Firefox .
I am using ubuntu 10.10 
firefox ask to download plug-ins and can not find or install them.
the applets failed to load.
I hear about there is JRE replace Jinititor on windows
can any one help me?
Thanks in advance

---

### Post by eng.ahmedgaber on 2011-05-10
nothing there >>>>>>>>>>>>
help me

---

### Post by eng.ahmedgaber on 2011-05-11
please try to help me
i really need help

---

### Post by AngelVer on 2011-08-08
Hi.

First of all... apologize for my english, this is my first english post,

Beginning with the trick... you need uninstall OpenJDK, if it's installed.

Then, you install *sun-java6-jre, sun-java6-jdk and sun-java6-plugin* on your terminal,

***sudo apt-get install sun-java6-jre sun-java6-jdk sun-java6-plugin***

If you are using Firefox, you need to know what version of jre are using your oracle server or applet, for that... try to open your applet again, when firefox indicates that you need install java plugin... press right button of your mouse, and on the contextual menu select *view source code of this page* and search the line that looks like this:
 var xsunpluginversion   = "1.5.0_18"

That's  the version that you need to change on your browser
In my case i installed java version 6 update 23, but my oracle server works with java version 5 update 18

As in your browser is registered the actual version it's necessary to change to the old version or the version that your server works

To change the java version of your browser go to:

*** /home/"youraccount"/.mozilla/firefox/"somedirectorywithextension.default***"

in that strange directory there is a file named pluginreg.dat, edit that file with the mousepad, notepad, vim or whatever you use. 

Find 2 lines that contain the version of the applets, something like this:

*application/x-java-applet;jpi-version=**1.6.0_23**:Java&#153 Plug-in::$*

change it to:

[I]application/x-java-applet;jpi-version=**1.5.0_18**:Java&#153 Plug-in::$r

[/I]repeat the last instruction in the other line:

*application/x-java-bean;jpi-version=**1.6.0_23**:Java&#153 Plug-in::$*

Save it and... close.

Finally try to open your oracle applet.

Tell me if that works to you.

Saludos desde México...

---

