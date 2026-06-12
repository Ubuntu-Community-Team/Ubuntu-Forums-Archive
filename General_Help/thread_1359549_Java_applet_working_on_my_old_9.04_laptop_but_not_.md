---
title: "Java applet working on my old 9.04 laptop but not on a new 9.10 installation"
date: 2009-12-19
forum: General Help
---

### Post by bgryderclock on 2009-12-19
I am setting up a new Ubuntu 9.10 laptop for a xmas gift. The Java-powered Facebook picture album creator is not working. It is only displaying a gray box.

The Java-powered Facebook picture album creator works correctly in on my other Ubuntu 9.04 laptop.

How do it find out what "Java-guts" are working correctly on the 9.04 installation and set up the 9.10 installation the same way?

---

### Post by USB_NL on 2009-12-19
hi

goto system>administration> synaptic package manager then search on the word java

i think the one you need to mark for install is sun-java6-jre

check this package on your older system 

ok?

---

### Post by bgryderclock on 2009-12-19
> **USB_NL said:**
> hi

goto system>administration> synaptic package manager then search on the word java

i think the one you need to mark for install is sun-java6-jre
check this package on your older system 
ok?
Thanks for the replu USB_NL,

I installed sun-java6-jre and all the Java stuff that I could find on the working laptop synaptic package manager setting. I read some stuff about Java versions, here are the Java version on the problematic and working machines.

problematic 9.10 laptop:
```
user@TbonezLinuxLappy:~$ sudo update-alternatives --config java
There are 3 choices for the alternative java (providing /usr/bin/java).

  Selection    Path                                      Priority   Status
------------------------------------------------------------
* 0            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1            /usr/lib/jvm/java-1.5.0-sun/jre/bin/java   53        manual mode
  2            /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  3            /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode

Press enter to keep the current choice[*], or type selection number
```

working 9.04 laptop:
```
user@LinuxLappyG41:/usr/lib/jvm$ sudo update-alternatives --config java
[sudo] password for user:

There are 6 alternatives which provide `java'.

  Selection    Alternative
-----------------------------------------------
*         1    /usr/lib/jvm/java-6-sun/jre/bin/java
 +        2    /usr/lib/jvm/java-6-openjdk/jre/bin/java
          3    /usr/lib/jvm/java-1.5.0-sun/jre/bin/java
          4    /usr/bin/gij-4.2
          5    /usr/bin/gij-4.3
          6    /usr/lib/jvm/java-gcj/jre/bin/java

Press enter to keep the default[*], or type selection number:
```

Edit: it is giving me this error now:
```
Exception: java.lang.ClassNotFoundException: com.facebook.facebookphotouploader5.FacebookPhotoUploader5.class
```


How do I verify and change which version of Java that Firefox is using for the applet?

---

### Post by nadazero on 2009-12-20
To see which version is used in firefox enter this in the address field:
```
about:plugins
```
or go to [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1) 

Did you install sun-java6-plugin?

I don't think the "update-alternatives java" affects which version firefox uses, because even though sudo update-alternatives --config java
on my machine reports 
* 0 /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1 /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  2 /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode
firefox uses "Version 6 Update 15" according to [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1) 
which seems to match the "Java(TM) Plug-in 1.6.0_15" I see in ```
about:plugins
```

---

### Post by bgryderclock on 2009-12-23
> **nadazero said:**
> To see which version is used in firefox enter this in the address field:
```
about:plugins
```
or go to [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1) 

Did you install sun-java6-plugin?

I don't think the "update-alternatives java" affects which version firefox uses, because even though sudo update-alternatives --config java
on my machine reports 
* 0 /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      auto mode
  1 /usr/lib/jvm/java-6-openjdk/jre/bin/java   1061      manual mode
  2 /usr/lib/jvm/java-6-sun/jre/bin/java       63        manual mode
firefox uses "Version 6 Update 15" according to [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1) 
which seems to match the "Java(TM) Plug-in 1.6.0_15" I see in ```
about:plugins
```

Thanks for the reply nadazero, 

about:****plugins on the problematic laptop shows:
**IcedTea java Web Browser 1.6.1 (6b16-1.6.1-3ubuntu1)** and
**JAVA(TM) Plug-in 1.6.0_16**

about:****plugins on the working one is shows only:
**IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu12)**
 
I'm working on stripping everything out and setting up only IcedTea Java Web Browser Plugin 1.4.1 (6b14-1.4.1-0ubuntu12)


Do you know of an easy way to do this? I keep trying to uninstall the default version and use force version to get 6b14-1.4.1-0ubuntu12, but The firefox plugin manager keeps reinstalling 6b16-1.6.1-3ubuntu1. (GRRRR!)

---

