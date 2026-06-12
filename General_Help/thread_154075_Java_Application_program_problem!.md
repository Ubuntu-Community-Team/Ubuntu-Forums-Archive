---
title: "Java Application program problem!"
date: 2006-04-02
forum: General Help
---

### Post by s_spiff on 2006-04-02
hey, i installed j2re and dunno why but every time i want to get azureus to start I get this error  :

```
alok@ubuntu:~$ azureus
Exception in thread "main" java.lang.UnsatisfiedLinkError: no swt-pi-gtk-3139 in java.library.path
        at java.lang.ClassLoader.loadLibrary(Unknown Source)
        at java.lang.Runtime.loadLibrary0(Unknown Source)
        at java.lang.System.loadLibrary(Unknown Source)
        at org.eclipse.swt.internal.Library.loadLibrary(Library.java:123)
        at org.eclipse.swt.internal.gtk.OS.<clinit>(OS.java:19)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
        at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
        at org.eclipse.swt.widgets.Display.<clinit>(Display.java:122)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:75)
        at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:58)
        at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:108)
        at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:147)
        at org.gudy.azureus2.ui.swt.Main.main(Main.java:162)

```

and when I run FrostWire I get something like java something something. Any Ideas to what I can do ?

---

### Post by marsanpin on 2006-04-07
Sorry I can't help you.
I myself have a similar problem; this one looks associated with some libgc
? version.
It tells me this:

mario@ubuntu01:~/Music Library$ ./master.script
Exception in thread "main" java.lang.NoClassDefFoundError: while resolving class : ml_master
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/l ibgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5ErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang12LinkageErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang20NoClassDefFoundErrorC1EPNS0_6StringE (/usr/lib/libgcj.so.6 .0.0)
   at ._ZN4java4lang13VMClassLoader18transformExceptionEPNS0_5ClassEPNS0_9Throwa bleE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang13VMClassLoader12resolveClassEPNS0_5ClassE (/usr/lib/libgcj. so.6.0.0)
   at ._ZN4java4lang5Class15initializeClassEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang5Class7forNameEPNS0_6StringEbPNS0_11ClassLoaderE (/usr/lib/l ibgcj.so.6.0.0)
   at ._ZN3gnu4java4lang10MainThread3runEv (/usr/lib/libgcj.so.6.0.0)
   at ._Z13_Jv_ThreadRunPN4java4lang6ThreadE (/usr/lib/libgcj.so.6.0.0)
   at ._Z11_Jv_RunMainP14_Jv_VMInitArgsPN4java4lang5ClassEPKciPS6_b (/usr/lib/li bgcj.so.6.0.0)
   at .main (/usr/lib/libgij.so.6.0.0)
   at .__libc_start_main (/lib/tls/i686/cmov/libc-2.3.5.so)
Caused by: java.lang.ClassNotFoundException: xm_master not found in gnu.gcj.runt ime.SystemClassLoader{urls=[file:./,file:./,file:./tritonus_share.jar,file:./jl1 .0.jar,file:./,file:./mp3spi1.9.2.jar,file:./jmactritonusspi.jar,file:./,file:./ jflac-1.1.jar], parent=gnu.gcj.runtime.ExtensionClassLoader{urls=[], parent=null }}
   at ._ZN4java4lang11VMThrowable16fillInStackTraceEPNS0_9ThrowableE (/usr/lib/l ibgcj.so.6.0.0)
   at ._ZN4java4lang9Throwable16fillInStackTraceEv (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ThrowableC1EPNS0_6StringEPS1_ (/usr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang9ExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/usr/lib/libgcj. so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringEPNS0_9ThrowableE (/u sr/lib/libgcj.so.6.0.0)
   at ._ZN4java4lang22ClassNotFoundExceptionC1EPNS0_6StringE (/usr/lib/libgcj.so .6.0.0)
   at ._ZN4java3net14URLClassLoader9findClassEPNS_4lang6StringE (/usr/lib/libgcj .so.6.0.0)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringEb (/usr/lib/libgcj.so.6 .0.0)
   at ._ZN4java4lang11ClassLoader9loadClassEPNS0_6StringE (/usr/lib/libgcj.so.6. 0.0)
   at ._Z13_Jv_FindClassP13_Jv_Utf8ConstPN4java4lang11ClassLoaderE (/usr/lib/lib gcj.so.6.0.0)
   at ._Z26_Jv_FindClassFromSignaturePcPN4java4lang11ClassLoaderE (/usr/lib/libg cj.so.6.0.0)
   at ._ZN20_Jv_BytecodeVerifier8pop_typeENS_4typeE (/usr/lib/libgcj.so.6.0.0)
   at ._ZN20_Jv_BytecodeVerifier21verify_instructions_0Ev (/usr/lib/libgcj.so.6. 0.0)
   at ._Z16_Jv_VerifyMethodP16_Jv_InterpMethod (/usr/lib/libgcj.so.6.0.0)
   at ._ZN21_Jv_InterpreterEngine9do_verifyEPN4java4lang5ClassE (/usr/lib/libgcj .so.6.0.0)
   at ._ZN10_Jv_Linker12verify_classEPN4java4lang5ClassE (/usr/lib/libgcj.so.6.0 .0)
   at ._ZN10_Jv_Linker14wait_for_stateEPN4java4lang5ClassEi (/usr/lib/libgcj.so. 6.0.0)
   ...8 more
mario@ubuntu01:~/Music Library$


Hope some Ubuntuers know some stuff about java an lib's;
The developer of the application "MusicLibrary" can not sort out what this error could be as you may all check below:

Hi Mario -

I have no clear idea what is happening here.  You may need help from 
someone with more Linux knowledge and experience than I have.  Maybe 
there is somebody local you can ask for help?

It *APPEARS* that you are in the correct directory (Music Library) and 
are invoking the correct script (./master.script).  It then appears that 
some version of Java is being invoked, but that it cannot find the Music 
Library "main method", which is in the file "ml_master.class".  However, 
the script (./master.script) contains "-cp .:./tritonus_share.jar:...". 
  This tells java where to look for "class files" (Java code files), and 
specifically, it tells Java that the FIRST place it should look is in 
the current directory (Music Library) -- that is what the "." means 
right after the "-cp ".

I don't recognize the file "/usr/lib/libgcj.so.6.0.0" that appears in 
all your "stack trace" entries.  I don't recall seeing anything like 
this when Java is installed on a Linux system.  It almost suggests that 
you have installed somebody's Java compiler, not a runtime (JRE).

Possibly you should try deleting the "java" that you have and then 
download one from the Sun Web site.  (I also don't understand what 
"certified" means in the context of installing a Java runtime.)


From the above, I followed the instructions and dowloaded sun-j2re1.5 from [http://users.lichtsnel.nl/~seveas/](http://users.lichtsnel.nl/~seveas/) using Synaptic
???

Can someone help here?:(

---

### Post by nanotube on 2006-04-07
dont know about the second problem... 

but for azureus, you have to be running on the official sun jre, the default jre that comes with ubuntu did not work for me.
also, you have to download the swt toolkit, if you are using the .jar install.
go to the link in my sig, and go to the "install azureus" section, it might help you out. (also the "install sun jre" section)

---

### Post by marsanpin on 2006-04-09
I found out (through some good post/tutorial in Ubuntu-forum-PT/BR section; sorry I can't remember who from :-() that one needs to tell java which version of j2re must be used as virtual machine.
Solved.:D 
Thanks for the interest and support.

Mario

---

