---
title: "Problems Installing/Upgrading/Launching Vuze"
date: 2011-05-16
forum: General Help
---

### Post by disco.sleeze on 2011-05-16
Hi guys,

I am a Ubuntu novice (at best) so the "idiot's guide" of fixing this problem would be most helpful.

I recently installed Vuze from the Ubuntu Software Center. The day after that, I logged in and it recommended I upgrade so I followed steps on the Vuze wiki for upgrading.

I am afraid I messed up at one step. Now Vuze won't launch at all when I select it from the program menu. When I attempt to launch Vuze in Terminal, this is the output I receive:

> CompilerOracle: exclude com/aelitis/net/udp/uc/impl/PRUDPPacketHandlerImpl$5.runSupport
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2.15.jar ; file:/usr/share/java/commons-cli-1.1.jar ; file:/usr/share/java/swt.new.jar ; file:/home/aron/
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
DEBUG::Mon May 16 10:37:55 CDT 2011::org.gudy.azureus2.ui.swt.mainwindow.SWTThread::createInstance::67:
  Loading SWT Libraries failed. Typical causes:

(1) swt.jar is not for your os architecture (i386).  You can get a new swt.jar (Min Version: 3.6) from [http://eclipse.org/swt](http://eclipse.org/swt)

(2) No write access to '/tmp'. SWT will extract libraries contained in the swt.jar to this dir.

    Initializer::<init>::111,Main::<init>::88,Main::main::255,NativeMethodAccessorImpl::invoke0::-2,NativeMethodAccessorImpl::invoke::57,DelegatingMethodAccessorImpl::invoke::43,Method::invoke::616,Main::directLaunch::229,Main::main::132,NativeMethodAccessorImpl::invoke0::-2,NativeMethodAccessorImpl::invoke::57,DelegatingMethodAccessorImpl::invoke::43,Method::invoke::616,MainExecutor$1::run::37,Thread::run::636
java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:194)
	at org.eclipse.swt.internal.Library.loadLibrary(Library.java:174)
	at org.eclipse.swt.internal.C.<clinit>(C.java:21)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
	at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
	at org.eclipse.swt.widgets.Display.<clinit>(Display.java:132)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.<init>(SWTThread.java:90)
	at org.gudy.azureus2.ui.swt.mainwindow.SWTThread.createInstance(SWTThread.java:67)
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:111)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.gudy.azureus2.ui.common.Main.directLaunch(Main.java:229)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:132)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)

I really appreciate any help you guys can give me. This forum has always been a great resource so I am remaining hopeful this can be resolved! :)

---

### Post by gordintoronto on 2011-05-16
I looked at the wiki, and couldn't find anything about upgrading. Where is it? Does it say anything specific about Ubuntu?

"swt.jar is not for your os architecture (i386)." means you have the wrong version. Delete what you have and try again.

---

### Post by disco.sleeze on 2011-05-17
I've uninstalled Vuze in both the software center and in Terminal.

I think I may just give up. This is obviously over my head.

---

