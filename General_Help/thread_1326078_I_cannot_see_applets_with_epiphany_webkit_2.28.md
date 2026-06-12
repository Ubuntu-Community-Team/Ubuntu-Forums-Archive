---
title: "I cannot see applets with epiphany webkit 2.28"
date: 2009-11-14
forum: General Help
---

### Post by claracc on 2009-11-14
Hello, I have the following problem with epiphany webkit 2.28 browser:

It doesn't show applets , ie [http://www.walter-fendt.de/ph14e/equilibrium.htm](http://www.walter-fendt.de/ph14e/equilibrium.htm), it doesn't show the saqure with the animated images, only text.
I have installed manually the following java software:

clara@clara1:~$ java -version
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Server VM (build 14.2-b01, mixed mode)

Firefox 3.5.5 shows perfectly well java applets, i type about:plugins and it shows:

Java(TM) Plug-in 1.6.0_15

    Nombre del fichero: /usr/lib/jvm/java-6-sun-1.6.0.15/jre/lib/i386/libnpjp2.so
    The next generation Java plug-in for Mozilla browsers.

Reading posts, it seems that a link is lost between epiphany plugins folder ( which i don't find) and the java library used. But i don't know how to do it. Or in other words, epiphany doesn't know about java plugins.

Could someone tell me how i say to epiphany webkit 2.28 to use the java plugin, please?

I have tried the following: system, preferences, sun java 6 plugin control panel, advanced, statement to run the default browser and then i write /usr/bin/epiphany-browser but it doesn't work

Thanks in advance.

---

### Post by claracc on 2009-11-15
Bump....?

Nobody can tell something about java and epiphany webkit 2.28?

Any idea is welcome.

---

### Post by epistemolos on 2009-12-02
I too have this problem.  

I am running an up to date Release 9.10 (karmic)

Kernel: 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:53:52 UTC 2009 x86_64 GNU/Linux

ii  sun-java6-bin                6-15-1                       Sun Java(TM) Runtime Environment (JRE) 6 (architecture dependent files)
un  sun-java6-demo               <none>                       (no description available)
ii  sun-java6-doc                6-15-1                       Sun JDK(TM) Documention -- integration installer
un  sun-java6-fonts              <none>                       (no description available)
ii  sun-java6-jdk                6-15-1                       Sun Java(TM) Development Kit (JDK) 6
ii  sun-java6-jre                6-15-1                       Sun Java(TM) Runtime Environment (JRE) 6 (architecture independent files
ii  sun-java6-plugin             6-15-1                       The Java(TM) Plug-in, Java SE 6
ii  sun-java6-source             6-15-1                       Sun Java(TM) Development Kit (JDK) 6 source files
un  sun-java6-src                <none>                       (no description available)

||/ Name                         Version                      Description
+++-============================-============================-========================================================================
ii  epiphany-browser             2.28.0-4ubuntu1              Intuitive GNOME web browser
ii  epiphany-browser-data        2.28.0-4ubuntu1              Data files for the GNOME web browser
un  epiphany-extension-gwget     <none>                       (no description available)
ii  epiphany-extensions          2.28.0-1                     Extensions for Epiphany web browser
un  epiphany-gecko               <none>                       (no description available)
ii  epiphany-webkit              2.28.0-4ubuntu1              Dummy, transitional package
un  epiphany-webkit-data         <none>                       (no description available)

---

### Post by sokleidas on 2009-12-05
I may join, epiphany also doesn't show the applets on this site: 
[http://epigraphy.packhum.org/inscriptions/main](http://epigraphy.packhum.org/inscriptions/main)

ludwigmeier@ludwigmeier-laptop:~$ java -version
java version "1.6.0_16"
Java(TM) SE Runtime Environment (build 1.6.0_16-b01)
Java HotSpot(TM) Server VM (build 14.2-b01, mixed mode)

Any help is appreciated, thanks in advance.

---

### Post by JakcV on 2009-12-21
I also have the similar problem, the epiphany can't show java. I tried it at several java testing websitehttp://www.javatester.org/

---

### Post by fragos on 2009-12-21
I get the same results in Chromium and Firefox 3.5. A Java Virtual Machine is required and if the site developers use MS Windows an Active-X wrapper may be the problem. Active-X is the proprietary MS substitute for Javascript and isn't supported in Linux.

---

### Post by claracc on 2009-12-22
I don't think the problem is a proprietary active X since I can see any applet with firefox 3.5.6 (i.e.:[http://www.walter-fendt.de/ph14e/equilibrium.htm](http://www.walter-fendt.de/ph14e/equilibrium.htm), this applet is shown in firefox 3.5.6 perfectly well).

I think epiphany webkit has not support for applets, unless epiphany-gecko had.

Is there a way to say epiphany-webkit to use the sun jre plugin to see applets, as it can be done in firefox?

---

### Post by Yellow Pasque on 2009-12-22
No, the sun-java6 plugin uses Mozilla-specific functions AFAICT.

---

### Post by deepclutch on 2010-01-15
I am having java 7(beta) installed and Epiphany-webkit nor Midori detects Java.Do I have to symlink firefox plugins directory to somewhere epiphany? :S

---

