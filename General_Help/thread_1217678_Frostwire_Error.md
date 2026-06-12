---
title: "Frostwire Error"
date: 2009-07-19
forum: General Help
---

### Post by Unanimated on 2009-07-19
I figured I would probably get better support if I submitted this problem on these forums as opposed to Frostwire's forums, so this is my problem.
I downloaded the Frostwire .deb package from frostwire.com, then installed it using GDebi. It installed Java and all that (Note that I do have ubuntu-restricted-extras installed, and that never came up with a Java prompt like it normally does), but attempting to open Frostwire gives me this error:

```
FrostWire version 4.17
Java version 1.6.0_14 from Sun Microsystems Inc.
Linux v. 2.6.28-13-generic on i386
Free/total memory: 2425024/5849088

java.lang.NoClassDefFoundError: Could not initialize class com.limegroup.gnutella.gui.GUIMediator
	at com.limegroup.gnutella.bugs.LocalClientInfo.<init>(Unknown Source)
	at com.limegroup.gnutella.gui.LocalClientInfoFactoryImpl.createLocalClientInfo(Unknown Source)
	at com.limegroup.gnutella.bugs.FatalBugManager.handleFatalBug(Unknown Source)
	at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ExceptionInInitializerError
	at com.limegroup.gnutella.gui.ResourceManager.setLocaleOptions(Unknown Source)
	at com.limegroup.gnutella.gui.ResourceManager.resetLocaleOptions(Unknown Source)
	at com.limegroup.gnutella.gui.ResourceManager.<clinit>(Unknown Source)
	at com.limegroup.gnutella.gui.GUIMediator.getThemeImage(Unknown Source)
	at com.limegroup.gnutella.gui.LimeJFrame.initialize(Unknown Source)
	at com.limegroup.gnutella.gui.LimeJFrame.<init>(Unknown Source)
	at com.limegroup.gnutella.gui.GUIMediator.<clinit>(Unknown Source)
	at com.limegroup.gnutella.gui.Initializer.installResources(Unknown Source)
	at com.limegroup.gnutella.gui.Initializer.initialize(Unknown Source)
	... 6 more
Caused by: java.util.MissingResourceException: Resource bundle not found
	at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
	at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
	at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
	at org.xnap.commons.i18n.I18nFactory.getI18n(Unknown Source)
	at com.limegroup.gnutella.gui.I18n.<clinit>(Unknown Source)
	... 15 more

STARTUP ERROR!


```
I've installed it twice now. I don't know what packages I should reinstall or anything-can anyone help?

---

### Post by michy99 on 2009-07-19
Maybe something on this page will help.

[https://help.ubuntu.com/community/FrostWire](https://help.ubuntu.com/community/FrostWire)

---

### Post by Unanimated on 2009-07-19
Nope, nothing on that page helped. Thanks, though.

---

### Post by Unanimated on 2009-07-19
Problem solved. Not sure what I really did, but I followed the instructions on [this]("http://forum.frostwire.com/viewtopic.php?f=1&t=6241") page up to step 5, then I quit Frostwire and opened it under my own account (it opened as root for some strange reason).

---

