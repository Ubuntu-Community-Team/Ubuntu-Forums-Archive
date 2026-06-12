---
title: "Vuze doesn't work anymore..."
date: 2010-05-02
forum: General Help
---

### Post by Zaytoven on 2010-05-02
Well I updated from 9.04 to 10.04 and Vuze does not open for me anymore when i click it. Is there anything that got thrown out that I need to install to get it back going for me? Any help would be greatly appreciated.:guitar:

---

### Post by WorMzy on 2010-05-02
Do you get an error message when you run it from a terminal?

I don't see Vuse in the repositories, so all I can suggest is downloading the source from the official website and trying to reinstall it using that.

---

### Post by 1b1 on 2010-05-04
I have the same problem: after the upgrade from 9.10 to 10.04 (32 bit) Vuze stopped working, I click on the icon and nothing happens. And Vuze is still installed.
What can I do? I don't want to lose the files... Thanks for the help in advance.

---

### Post by StolenPie on 2010-05-04
same problem

---

### Post by bensexson on 2010-05-04
I had the same problem.  I just uninstalled and reinstalled it with the Ubuntu Software center and it started working again.

---

### Post by headlessspider on 2010-05-04
i can confirm bensexon's observation. i uninstalled azureus/vuze via software center and then installed it again. now it starts up properly.

---

### Post by 1b1 on 2010-05-04
Thank You.

---

### Post by makebeernoatwar on 2010-06-03
Uninstall / reinstall didn't work for me.  When I Completely Removed Vuze, it was still showing in my Applications>Internet menu.  

Other threads suggest this might be a Java-related problem.  Does that give anyone ideas?

---

### Post by URGettingADull on 2010-06-06
nope, just corroborating.

---

### Post by sXeChris on 2010-06-06
I think they're working on it, Lucid has kept a lot of things from working. My guess is that updates are on the way.

---

### Post by portilhe on 2010-06-09
I have the same problem, vuze won't start for me. I tried uninstalling adn reinstalling and it didn't solve it. I thik it is java related because when I try to start it from the terminal I get the following:
```
portilhe@gavdos:~$ vuze
[warning] /usr/bin/vuze: Unable to locate swt in /usr/share/java
file:/usr/lib/jni/ ; file:/usr/lib/java/ ; file:/usr/share/java/Azureus2.jar ; file:/usr/share/java/log4j-1.2-1.2.15.jar ; file:/usr/share/java/commons-cli-1.2.jar ; file:/home/portilhe/
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
	at java.lang.ClassLoader.loadClassInternal(ClassLoader.java:334)
	... 15 more
Start fails:
com.aelitis.azureus.core.AzureusCoreException: Azureus core already instantiated
	at com.aelitis.azureus.core.impl.AzureusCoreImpl.create(AzureusCoreImpl.java:120)
	at com.aelitis.azureus.core.AzureusCoreFactory.create(AzureusCoreFactory.java:46)
	at org.gudy.azureus2.ui.common.Main.main(Main.java:160)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.aelitis.azureus.launcher.MainExecutor$1.run(MainExecutor.java:37)
	at java.lang.Thread.run(Thread.java:636)

```

Please, help!
-m

---

### Post by karl_yap on 2010-06-18
I have the same problem with Vuze not starting after upgrading to Ubuntu 10.04.  However this fix works for me by creating a symbolic link:

sudo ln -s /usr/share/java/swt-gtk-3.5.1.jar swt.jar

After creating this link, Vuze will start.

---

### Post by portilhe on 2010-06-22
Thanks a lot! That worked like a charm.

---

### Post by cynicalcylon on 2010-06-22
Phew!
Uninstall/Reinstall worked fine for me.
Thought I might have lost some files I started this morning before deciding to hit the new upgrade.

Ta guys.

---

### Post by Milos_SD on 2010-06-22
I have simmilar problem. But my problem is that when I start Vuze, I get only Azureus, and not the Vuze interface with Vuze HD network options. But if I start Vuze with sudo, or gksu, I have Vuze interface and Vuze HD network.

---

