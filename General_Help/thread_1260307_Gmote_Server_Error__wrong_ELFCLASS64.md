---
title: "Gmote Server Error  wrong ELFCLASS64"
date: 2009-09-07
forum: General Help
---

### Post by hendrik r g on 2009-09-07
Hello World!

I really really like the Gmote and want to use it. It used to work fine on an older system with ubuntu 8.10 32bit. Now i need it on a newer system Ubuntu 9.04 - 64bit Kernel is 2.6.28-15 Generic. VLC (as almost everything else) is unmodified standard installtion. 


 Unfortunately the server starts 
 with a error msg: Unable to load library 'vlc': /usr/lib/libvlc.so. 
 2.1.0: wrong ELF class: ELFCLASS64 
 


The icon apears but the server never becomes findable for my Phone. 
 


Here ist the Console output: 
 ~/GmoteServerLinux2.0.0$ 06.09.2009 18:57:49 
 org.gmote.server.GmoteServerUi sharedMain 
 WARNUNG: Gmote Version: 2.0.0 
 06.09.2009 18:57:49 org.gmote.server.GmoteServerUi sharedMain 
 WARNUNG: OperatingSystem: Linux 
 06.09.2009 18:57:49 org.gmote.server.MulticastServerThread run 
 INFO: Listening for udp packets on 9901 
 06.09.2009 18:57:49 
 org.gmote.server.settings.SupportedFiletypeSettings <init> 
 INFO: Initializing supported file types settings. 
 06.09.2009 18:57:49 
 org.gmote.server.settings.SupportedFiletypeSettings <init> 
 INFO: Done initializing supported file types settings. 
 06.09.2009 18:57:49 org.gmote.server.media.MediaPlayerManager 
 createNewMediaPlayerInstance 
 INFO: Creating media player with name: 
 org.gmote.server.media.vlc.VlcMediaPlayer 
 06.09.2009 18:57:49 org.gmote.server.GmoteServerUi sharedMain 
 SCHWERWIEGEND: Unable to load library 'vlc': /usr/lib/libvlc.so.2.1.0: Gmote
 wrong ELF class: ELFCLASS64 
 java.lang.UnsatisfiedLinkError: Unable to load library 'vlc': /usr/lib/ 
 libvlc.so.2.1.0: wrong ELF class: ELFCLASS64 
         at com.sun.jna.NativeLibrary.loadLibrary(NativeLibrary.java:127) 
         at com.sun.jna.NativeLibrary.getInstance(NativeLibrary.java:170) 
         at com.sun.jna.Library$Handler.<init>(Library.java:123) 
         at com.sun.jna.Native.loadLibrary(Native.java:260) 
         at com.sun.jna.Native.loadLibrary(Native.java:246) 
         at org.videolan.jvlc.internal.LibVlc.<clinit>(LibVlc.java:41) 
         at org.videolan.jvlc.JVLC.<init>(JVLC.java:45) 
         at org.gmote.server.media.vlc.VlcMediaPlayer.initialise 
 (VlcMediaPlayer.java:70) 
         at 
 org.gmote.server.media.MediaPlayerManager.createNewMediaPlayerInstance 
 (MediaPlayerManager.java:102) 
         at org.gmote.server.media.MediaPlayerManager.getMediaPlayerInstance 
 (MediaPlayerManager.java:91) 
         at org.gmote.server.media.MediaPlayerManager.getMediaPlayer 
 (MediaPlayerManager.java:58) 
         at org.gmote.server.media.MediaPlayerManager.initialize 
 (MediaPlayerManager.java:47) 
         at org.gmote.server.GmoteServer.startServer(GmoteServer.java:94) 
         at org.gmote.server.GmoteServerUi.sharedMain(GmoteServerUi.java:334) 
         at org.gmote.server.GmoteServerUiLinux.main(GmoteServerUiLinux.java: 
 36) 
 

 VLC is unmodified standard installtion 
 
Anyone had the same issue? Help? Please?? :D

---

### Post by hendrik r g on 2009-09-08
I still wasn't able to find a solution. I updated VLC to version 1.0.1 and with it its Libs. The msg remains the same with updated version number:
Unable to load library 'vlc': /usr/lib/libvlc.so. 
 2.2.0: wrong ELF class: ELFCLASS64 

Anyone ideas? please?

---

### Post by jahwah on 2009-12-13
Hello,

You have to force java version.
When you run GmoteServer.sh it run :
java -classpath bin:lib/jna.jar:lib/slf4j-api-1.5.3.jar:lib/swing-worker-1.2.jar org.gmote.server.GmoteServerUiLinux &

I think java in your classpath is not 64bits java.

To fix your problem, edit GmoteServer.sh, and replace line
java -classpath bin:lib/jna.jar:lib/slf4j-api-1.5.3.jar:lib/swing-worker-1.2.jar org.gmote.server.GmoteServerUiLinux &
by
/usr/lib/jvm/java-6-sun/jre/bin/java -classpath bin:lib/jna.jar:lib/slf4j-api-1.5.3.jar:lib/swing-worker-1.2.jar org.gmote.server.GmoteServerUiLinux &

(/usr/lib/jvm/java-6-sun/jre/bin/java is my 64 bits jre, replace by yours)

JW

---

