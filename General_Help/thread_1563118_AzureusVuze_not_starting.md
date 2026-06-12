---
title: "Azureus/Vuze not starting"
date: 2010-08-28
forum: General Help
---

### Post by bigred1 on 2010-08-28
The GUI button to launch Azureus/Vuze does nothing. When I try to run it from the command line I get the output below. Note that I don't have too much already listeting on ports. netstat -a shows only the following as "LISTENING". 

I just now updated to Ubuntu 10.4, which may be the cause of this.

```

fox@fox-desktop:/usr/bin$ netstat -a
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State      
tcp        0      0 localhost:ipp           *:*                     LISTEN     
tcp        0      0 *:9433                  *:*                     LISTEN     
tcp        0      0 *:51949                 *:*                     LISTEN     

```

```

fox@fox-desktop:/usr/bin$ azureus
[warning] /usr/bin/azureus: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/bin/
StartServer ERROR: unable to bind to a local port listening for passed torrent info: <>
StartSocket: passing startup args to already-running Azureus java process
java.io.EOFException
	at java.io.DataInputStream.readInt(DataInputStream.java:392)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.<init>(LocalSocketHelper.java:44)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.connect(LocalSocketHelper.java:68)
	at org.gudy.azureus2.ui.swt.StartSocket.sendArgs(StartSocket.java:59)
	at org.gudy.azureus2.ui.swt.Main.processParams(Main.java:222)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:82)
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
DEBUG::Sat Aug 28 23:25:11 IDT 2010::org.gudy.azureus2.ui.swt.StartSocket::sendArgs::80:
  java.io.EOFException
	at java.io.DataInputStream.readInt(DataInputStream.java:392)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.<init>(LocalSocketHelper.java:44)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.connect(LocalSocketHelper.java:68)
	at org.gudy.azureus2.ui.swt.StartSocket.sendArgs(StartSocket.java:59)
	at org.gudy.azureus2.ui.swt.Main.processParams(Main.java:222)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:82)
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

Impossible to bind to a local socket.
Loading of torrents via command line parameter will fail until this is fixed.
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
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
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Shell
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:111)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
	... 12 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Shell
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at com.aelitis.azureus.launcher.classloading.PrimaryClassloader.loadClass(PrimaryClassloader.java:103)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 15 more
StartServer ERROR: unable to bind to a local port for passed torrent info
StartSocket: passing startup args to already-running process.
java.io.EOFException
	at java.io.DataInputStream.readInt(DataInputStream.java:392)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.<init>(LocalSocketHelper.java:44)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.connect(LocalSocketHelper.java:68)
	at org.gudy.azureus2.ui.common.Main$StartSocket.<init>(Main.java:361)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:155)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)
fox@fox-desktop:/usr/bin$ ^C
fox@fox-desktop:/usr/bin$ clear

fox@fox-desktop:/usr/bin$ azureus 
[warning] /usr/bin/azureus: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/usr/bin/
StartServer ERROR: unable to bind to a local port listening for passed torrent info: <>
StartSocket: passing startup args to already-running Azureus java process
java.io.EOFException
	at java.io.DataInputStream.readInt(DataInputStream.java:392)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.<init>(LocalSocketHelper.java:44)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.connect(LocalSocketHelper.java:68)
	at org.gudy.azureus2.ui.swt.StartSocket.sendArgs(StartSocket.java:59)
	at org.gudy.azureus2.ui.swt.Main.processParams(Main.java:222)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:82)
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
DEBUG::Sat Aug 28 23:25:20 IDT 2010::org.gudy.azureus2.ui.swt.StartSocket::sendArgs::80:
  java.io.EOFException
	at java.io.DataInputStream.readInt(DataInputStream.java:392)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.<init>(LocalSocketHelper.java:44)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.connect(LocalSocketHelper.java:68)
	at org.gudy.azureus2.ui.swt.StartSocket.sendArgs(StartSocket.java:59)
	at org.gudy.azureus2.ui.swt.Main.processParams(Main.java:222)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:82)
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

Impossible to bind to a local socket.
Loading of torrents via command line parameter will fail until this is fixed.
changeLocale: *Default Language* != English (United States). Searching without country..
changeLocale: Searching for language English in *any* country..
changeLocale: no message properties for Locale 'English (United States)' (en_US), using 'English (default)'
java.lang.reflect.InvocationTargetException
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
Caused by: java.lang.NoClassDefFoundError: org/eclipse/swt/widgets/Shell
	at org.gudy.azureus2.ui.swt.mainwindow.Initializer.<init>(Initializer.java:111)
	at org.gudy.azureus2.ui.swt.Main.<init>(Main.java:88)
	at org.gudy.azureus2.ui.swt.Main.main(Main.java:255)
	... 12 more
Caused by: java.lang.ClassNotFoundException: org.eclipse.swt.widgets.Shell
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:321)
	at com.aelitis.azureus.launcher.classloading.PrimaryClassloader.loadClass(PrimaryClassloader.java:103)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
	... 15 more
StartServer ERROR: unable to bind to a local port for passed torrent info
StartSocket: passing startup args to already-running process.
java.io.EOFException
	at java.io.DataInputStream.readInt(DataInputStream.java:392)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.<init>(LocalSocketHelper.java:44)
	at org.gudy.azureus2.core3.util.LocalSocketHelper.connect(LocalSocketHelper.java:68)
	at org.gudy.azureus2.ui.common.Main$StartSocket.<init>(Main.java:361)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:155)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)
fox@fox-desktop:/usr/bin$ 


```

---

