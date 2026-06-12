---
title: "java.security.AccessControlException while running javaws"
date: 2010-07-08
forum: General Help
---

### Post by strattonbrazil on 2010-07-08
I'm trying to look at an example java-web start, which worked on my friend's Window machine, but at least one part fails on machine and I get the following error.  Is something misconfigured on my end?  

```

> javaws http://common.l2fprod.com/jnlp/demo.jnlp
java.security.AccessControlException: access denied (java.util.PropertyPermission javawebstart.version read)
	at java.security.AccessControlContext.checkPermission(AccessControlContext.java:342)
	at java.security.AccessController.checkPermission(AccessController.java:553)
	at java.lang.SecurityManager.checkPermission(SecurityManager.java:549)
	at net.sourceforge.jnlp.runtime.JNLPSecurityManager.checkPermission(JNLPSecurityManager.java:282)
	at java.lang.SecurityManager.checkPropertyAccess(SecurityManager.java:1302)
	at java.lang.System.getProperty(System.java:669)
	at com.l2fprod.common.demo.PropertySheetPage$BeanBeanInfo.<init>(PropertySheetPage.java:202)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at com.l2fprod.common.model.DefaultBeanInfoResolver.getBeanInfo(DefaultBeanInfoResolver.java:95)
	at com.l2fprod.common.model.DefaultBeanInfoResolver.getBeanInfo(DefaultBeanInfoResolver.java:69)
	at com.l2fprod.common.demo.PropertySheetPage.<init>(PropertySheetPage.java:64)
	at com.l2fprod.common.demo.PropertySheetMain.<init>(PropertySheetMain.java:42)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance0(Native Method)
	at sun.reflect.NativeConstructorAccessorImpl.newInstance(NativeConstructorAccessorImpl.java:57)
	at sun.reflect.DelegatingConstructorAccessorImpl.newInstance(DelegatingConstructorAccessorImpl.java:45)
	at java.lang.reflect.Constructor.newInstance(Constructor.java:532)
	at java.lang.Class.newInstance0(Class.java:372)
	at java.lang.Class.newInstance(Class.java:325)
	at com.l2fprod.common.demo.Main.addDemo(Main.java:78)
	at com.l2fprod.common.demo.Main.<init>(Main.java:53)
	at com.l2fprod.common.demo.Main.main(Main.java:100)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at net.sourceforge.jnlp.Launcher.launchApplication(Launcher.java:454)
	at net.sourceforge.jnlp.Launcher$TgThread.run(Launcher.java:731)
Disposing window


```

---

