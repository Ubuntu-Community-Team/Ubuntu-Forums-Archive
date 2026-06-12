---
title: "Chromium Icedtea (Java)"
date: 2010-11-17
forum: General Help
---

### Post by io5cml4z on 2010-11-17
[LEFT]I need help getting the icedtea java plugin to work properly on Chromium. When I go to [http://www.funorb.com/](http://www.funorb.com/) and go to Arcanists, I usually get to the login screen, and sometimes I'm even able to login, but right after that, it crashes with an error message (Something like Icedtea plugin crashed unexpectedly). Help? :(
[/LEFT]

---

### Post by io5cml4z on 2010-11-17
Anyone? :(

---

### Post by io5cml4z on 2010-11-17
Bump.

---

### Post by gandaran on 2010-11-18
openjdk-java doesn't always work well on every website, try removing all openjdk-java packages or just the icedtea plugin if you have any openjdk dependent applications installed and install sun-java instead.
to install sun-java enable the archive.canonical partner repository in software sources and update the software package list then you can find the sun-java6-plugin in package manager.

---

### Post by zaphod777 on 2010-11-18
also does it work in Firefox? What version of Chrome are you using?

---

### Post by xxs2010 on 2010-11-18
install sun-java6:
sudo add-apt-repository "deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner"
sudo apt-get update
sudo apt-get install sun-java6-jre sun-java6-plugin
sudo apt-get install sun-java6-jdk sun-java6-plugin
sudo update-alternatives --config java

sudo gedit /etc/enviroment
add next two lines to the file
CLASSPATH=.:/usr/lib/jvm/java-6-sun/lib
JAVA_HOME=/usr/lib/jvm/java-6-sun

sudo gedit /etc/jvm
fill the next line to the top
  /usr/lib/jvm/java-6-sun

sudo update-java-alternatives -s java-6-sun

---

### Post by io5cml4z on 2010-11-18
Sun java doesn't work at all for me, and when it *does* I have sound issues. And I'm using the latest Chromium build from the Chromium daily ppa. And it works *perfectly* in firefox, but right now I can't use that because it's lagging like crazy and it won't stop, but that's a separate issue. So, anyone know how I can get openjdk icedtea working on Chromium?

---

### Post by io5cml4z on 2010-11-18
I was searching on the forums and I tried this code in the terminal:
> LD_LIBRARY_PATH=/usr/lib/xulrunner-1.9.2.3/ chromium-browserjava version "1.6.0_20"
OpenJDK Runtime Environment (IcedTea6 1.9.1) (6b20-1.9.1-1ubuntu3)
OpenJDK 64-Bit Server VM (build 17.0-b16, mixed mode)
18-Nov-2010 8:07:07 PM com.sun.corba.se.impl.ior.IORImpl getProfile
WARNING: "IOP00511201: (INV_OBJREF) IOR must have at least one IIOP profile"
org.omg.CORBA.INV_OBJREF:   vmcid: SUN  minor code: 1201  completed: No
	at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:473)
	at com.sun.corba.se.impl.logging.IORSystemException.iorMustHaveIiopProfile(IORSystemException.java:495)
	at com.sun.corba.se.impl.ior.IORImpl.getProfile(IORImpl.java:334)
	at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:787)
	at com.sun.corba.se.impl.encoding.CDRInputStream_1_0.read_Object(CDRInputStream_1_0.java:761)
	at com.sun.corba.se.impl.encoding.CDRInputStream.read_Object(CDRInputStream.java:231)
	at com.sun.corba.se.impl.resolver.INSURLOperationImpl.getIORFromString(INSURLOperationImpl.java:120)
	at com.sun.corba.se.impl.resolver.INSURLOperationImpl.operate(INSURLOperationImpl.java:130)
	at com.sun.corba.se.impl.orb.ORBImpl.string_to_object(ORBImpl.java:836)
	at org.GNOME.Accessibility.AccessUtil.getRegistryObject(AccessUtil.java:143)
	at org.GNOME.Accessibility.JavaBridge.registerApplication(JavaBridge.java:1154)
	at org.GNOME.Accessibility.JavaBridge.<init>(JavaBridge.java:405)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at java.awt.Toolkit.loadAssistiveTechnologies(Toolkit.java:786)
	at java.awt.Toolkit.getDefaultToolkit(Toolkit.java:875)
	at java.awt.Window.getToolkit(Window.java:1170)
	at java.awt.Window.init(Window.java:400)
	at java.awt.Window.<init>(Window.java:438)
	at java.awt.Frame.<init>(Frame.java:419)
	at java.awt.Frame.<init>(Frame.java:384)
	at sun.awt.EmbeddedFrame.<init>(EmbeddedFrame.java:102)
	at sun.awt.EmbeddedFrame.<init>(EmbeddedFrame.java:99)
	at sun.awt.EmbeddedFrame.<init>(EmbeddedFrame.java:87)
	at sun.awt.X11.XEmbeddedFrame.<init>(XEmbeddedFrame.java:35)
	at sun.applet.PluginAppletViewer.<init>(PluginAppletViewer.java:379)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at sun.applet.PluginStreamHandler.<init>(PluginStreamHandler.java:85)
	at sun.applet.PluginMain.connect(PluginMain.java:155)
	at sun.applet.PluginMain.<init>(PluginMain.java:137)
	at sun.applet.PluginMain.main(PluginMain.java:116)
But same result. Oh, and I suppose I should mention, some java applets (like the java verifier) work, but none of the Jagex ones do (like Runescape and Funorb games, like Arcanists and Void Hunters). It just crashes with that chromium plugin crash message. :(

---

### Post by io5cml4z on 2010-11-18
Bump.

---

