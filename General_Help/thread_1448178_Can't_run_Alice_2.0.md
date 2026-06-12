---
title: "Can't run Alice 2.0"
date: 2010-04-06
forum: General Help
---

### Post by tyre_ on 2010-04-06
Hi,
I'm trying to run Alice 2.0, I followed the instructions on their website:
Run the command```
tar xvfz Alice-2.0.0.tar.gz
```Then run```
  cd Alice/Required
```Then```
 ./run-alice
```But when I try to run it I get the following error:
```
 ~/MyDownloads/Alice/Required$ ./run-alice
./run-alice: line 1: java: command not found
```Anyone know what the problem might be?

---

### Post by thebigob on 2010-04-06
in a console type the command java - version. You should see:

```

callum@callumlap:~$ java -version
java version "1.6.0_15"
Java(TM) SE Runtime Environment (build 1.6.0_15-b03)
Java HotSpot(TM) Server VM (build 14.1-b02, mixed mode)
callum@callumlap:~$ 

```

if not you will need to install Java onto your system.

---

### Post by tyre_ on 2010-04-06
I installed Java into my /usr/local directory.  Is this the right place to install it (I'm a ubuntu newbie).  When I type ./run-alice this is what I get:
```
:~/MyDownloads/Alice/Required$ ./run-alice
Unrecognised command line option: -Xincgc
Usage: java [-options] class [arg1 arg2 ...]
                 (to run a class file)
   or  java [-options] -jar jarfile [arg1 arg2 ...]
                 (to run a standalone jar file)

where options include:
  -client       compatibility (ignored)
  -server       compatibility (ignored)

  -cp           <jar/zip files and directories separated by :>
  -classpath       <jar/zip files and directories separated by :>
           locations where to find application classes
  -D<name>=<value> set a system property
  -verbose[:class|gc|jni]
           :class print out information about class loading, etc.
           :gc print out results of garbage collection
           :jni print out native method dynamic resolution
  -version       print out version number and copyright information
  -showversion     show version number and copyright and continue
  -fullversion     show jpackage-compatible version number and exit
  -? -help       print out this message
  -X           show help on non-standard options
swalker@tyre:~/MyDownloads/Alice/Required$ ^C
swalker@tyre:~/MyDownloads/Alice/Required$ 

```

---

### Post by thebigob on 2010-04-06
Sadly this could be very tricky to debug. 

Hopefully [this]("http://www.alice.org/community/showthread.php?t=1538") thread can help.

---

### Post by tyre_ on 2010-04-09
So I thought I'd try installing sun-java as that thread suggested, but it does this to my terminal:

```

Package configuration

 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java6-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;
 &#9474;                                                                           &#9474; 
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593; 
 &#9474;                                                                           &#9646; 
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618; 
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618; 
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618; 
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618; 
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618; 
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618; 
 &#9474;                                                                           &#9618; 
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618; 
 &#9474;     form, any other machine readable materials including, but not         &#9618; 
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595; 
 &#9474;                                                                             
 &#9474;                                  <Ok>                                       
 &#9474;                                                                           &#9474; 
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496; 
                                                                               
```and won't let me click or type ok or do anything.

---

