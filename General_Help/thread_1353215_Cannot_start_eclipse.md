---
title: "Cannot start eclipse"
date: 2009-12-12
forum: General Help
---

### Post by dannyek7 on 2009-12-12
I am running ubuntu 8.10. I had Eclipse running fine for months. I attempted to add some plugins and install a separate instance of 3.4

Since then, i get error messages whenever i try to start either eclipse (3.2 as added from the add/remove programs menu or 3.4) I am able to start either by doing sudo eclipse


Here is my error codes below:


!SESSION 2009-12-12 10:12:14.741 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.version=1.6.0_0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 2 1 2009-12-12 10:12:16.830
!MESSAGE NLS missing message: initializer_error in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-12-12 10:12:16.830
!MESSAGE NLS missing message: fileInitializer_fileNotFound in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-12-12 10:12:16.831
!MESSAGE NLS missing message: fileInitializer_IOError in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.osgi 2 1 2009-12-12 10:12:16.831
!MESSAGE NLS missing message: fileInitializer_missingFileName in: org.eclipse.core.internal.runtime.messages

!ENTRY org.eclipse.core.resources 2 10035 2009-12-12 10:12:17.462
!MESSAGE A workspace crash was detected. The previous session did not exit normally.

!ENTRY org.eclipse.osgi 4 0 2009-12-12 10:12:17.517
!MESSAGE An error occurred while automatically activating bundle org.eclipse.core.resources (99).
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.core.internal.compatibility.PluginActi vator.start() of bundle org.eclipse.core.resources.
    at org.eclipse.osgi.framework.internal.core.BundleCon  textImpl.startActivator(BundleContextImpl.java:101  0)
    at org.eclipse.osgi.framework.internal.core.BundleCon  textImpl.start(BundleContextImpl.java:966)
    at org.eclipse.osgi.framework.internal.core.BundleHos  t.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractB  undle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start  (SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.EclipseL  azyStarter.preFindLocalClass(EclipseLazyStarter.ja  va:8:cool:
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManag  er.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClass  Loader.findLocalClass(DefaultClassLoader.java:189)
    at org.eclipse.osgi.framework.internal.core.BundleLoa  der.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.SingleSou  rcePackage.loadClass(SingleSourcePackage.java:37)
    at org.eclipse.osgi.framework.internal.core.BundleLoa  der.findClass(BundleLoader.java:383)
    at org.eclipse.osgi.framework.internal.core.BundleLoa  der.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClass  Loader.loadClass(DefaultClassLoader.java:83)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:2  64)
    at java.lang.ClassLoader.loadClassInternal(ClassLoade  r.java:332)
    at org.eclipse.ui.internal.ide.IDEApplication.run(IDE  Application.java:96)
    at org.eclipse.core.internal.runtime.PlatformActivato  r$1.run(PlatformActivator.java:7
    at org.eclipse.core.runtime.internal.adaptor.EclipseA  ppLauncher.runApplication(EclipseAppLauncher.java:  92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseA  ppLauncher.start(EclipseAppLauncher.java:6
    at org.eclipse.core.runtime.adaptor.EclipseStarter.ru  n(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.ru  n(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ  e Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Native  MethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(De  legatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.core.launcher.Main.invokeFramework(Mai  n.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:  280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: org.eclipse.core.internal.dtree.ObjectNotFoundExce  ption: Tree element /TestAspect not found.
    at org.eclipse.core.internal.dtree.AbstractDataTree.h  andleNotFound(AbstractDataTree.java:257)
    at org.eclipse.core.internal.dtree.DeltaDataTree.getD  ata(DeltaDataTree.java:585)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBa  ckwardDelta(DataDeltaNode.java:50)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBa  ckwardDelta(DataDeltaNode.java:47)
    at org.eclipse.core.internal.dtree.DeltaDataTree.asBa  ckwardDelta(DeltaDataTree.java:8:cool:
    at org.eclipse.core.internal.dtree.DeltaDataTree.rero  ot(DeltaDataTree.java:816)
    at org.eclipse.core.internal.dtree.DeltaDataTree.rero  ot(DeltaDataTree.java:815)
    at org.eclipse.core.internal.dtree.DeltaDataTree.rero  ot(DeltaDataTree.java:792)
    at org.eclipse.core.internal.watson.ElementTree.immut  able(ElementTree.java:517)
    at org.eclipse.core.internal.resources.SaveManager.re  store(SaveManager.java:644)
    at org.eclipse.core.internal.resources.SaveManager.st  artup(SaveManager.java:1299)
    at org.eclipse.core.internal.resources.Workspace.star  tup(Workspace.java:1883)
    at org.eclipse.core.internal.resources.Workspace.open  (Workspace.java:1653)
    at org.eclipse.core.resources.ResourcesPlugin.startup  (ResourcesPlugin.java:367)
    at org.eclipse.core.internal.compatibility.PluginActi  vator.start(PluginActivator.java:31)
    at org.eclipse.osgi.framework.internal.core.BundleCon  textImpl$2.run(BundleContextImpl.java:991)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.eclipse.osgi.framework.internal.core.BundleCon  textImpl.startActivator(BundleContextImpl.java:985  )
    ... 28 more
Root exception:
org.eclipse.core.internal.dtree.ObjectNotFoundExce  ption: Tree element /TestAspect not found.
    at org.eclipse.core.internal.dtree.AbstractDataTree.h  andleNotFound(AbstractDataTree.java:257)
    at org.eclipse.core.internal.dtree.DeltaDataTree.getD  ata(DeltaDataTree.java:585)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBa  ckwardDelta(DataDeltaNode.java:50)
    at org.eclipse.core.internal.dtree.DataDeltaNode.asBa  ckwardDelta(DataDeltaNode.java:47)
    at org.eclipse.core.internal.dtree.DeltaDataTree.asBa  ckwardDelta(DeltaDataTree.java:8:cool:
    at org.eclipse.core.internal.dtree.DeltaDataTree.rero  ot(DeltaDataTree.java:816)
    at org.eclipse.core.internal.dtree.DeltaDataTree.rero  ot(DeltaDataTree.java:815)
    at org.eclipse.core.internal.dtree.DeltaDataTree.rero  ot(DeltaDataTree.java:792)
    at org.eclipse.core.internal.watson.ElementTree.immut  able(ElementTree.java:517)
    at org.eclipse.core.internal.resources.SaveManager.re  store(SaveManager.java:644)
    at org.eclipse.core.internal.resources.SaveManager.st  artup(SaveManager.java:1299)
    at org.eclipse.core.internal.resources.Workspace.star  tup(Workspace.java:1883)
    at org.eclipse.core.internal.resources.Workspace.open  (Workspace.java:1653)
    at org.eclipse.core.resources.ResourcesPlugin.startup  (ResourcesPlugin.java:367)
    at org.eclipse.core.internal.compatibility.PluginActi  vator.start(PluginActivator.java:31)
    at org.eclipse.osgi.framework.internal.core.BundleCon  textImpl$2.run(BundleContextImpl.java:991)
    at java.security.AccessController.doPrivileged(Native Method)
    at org.eclipse.osgi.framework.internal.core.BundleCon  textImpl.startActivator(BundleContextImpl.java:985  )
    at org.eclipse.osgi.framework.internal.core.BundleCon  textImpl.start(BundleContextImpl.java:966)
    at org.eclipse.osgi.framework.internal.core.BundleHos  t.startWorker(BundleHost.java:317)
    at org.eclipse.osgi.framework.internal.core.AbstractB  undle.start(AbstractBundle.java:256)
    at org.eclipse.osgi.framework.util.SecureAction.start  (SecureAction.java:342)
    at org.eclipse.core.runtime.internal.adaptor.EclipseL  azyStarter.preFindLocalClass(EclipseLazyStarter.ja  va:8:cool:
    at org.eclipse.osgi.baseadaptor.loader.ClasspathManag  er.findLocalClass(ClasspathManager.java:412)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClass  Loader.findLocalClass(DefaultClassLoader.java:189)
    at org.eclipse.osgi.framework.internal.core.BundleLoa  der.findLocalClass(BundleLoader.java:334)
    at org.eclipse.osgi.framework.internal.core.SingleSou  rcePackage.loadClass(SingleSourcePackage.java:37)
    at org.eclipse.osgi.framework.internal.core.BundleLoa  der.findClass(BundleLoader.java:383)
    at org.eclipse.osgi.framework.internal.core.BundleLoa  der.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClass  Loader.loadClass(DefaultClassLoader.java:83)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:2  64)
    at java.lang.ClassLoader.loadClassInternal(ClassLoade  r.java:332)
    at org.eclipse.ui.internal.ide.IDEApplication.run(IDE  Application.java:96)
    at org.eclipse.core.internal.runtime.PlatformActivato  r$1.run(PlatformActivator.java:7:cool:
    at org.eclipse.core.runtime.internal.adaptor.EclipseA  ppLauncher.runApplication(EclipseAppLauncher.java:  92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseA  ppLauncher.start(EclipseAppLauncher.java:6:cool:
    at org.eclipse.core.runtime.adaptor.EclipseStarter.ru  n(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.ru  n(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ  e Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Native  MethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(De  legatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.core.launcher.Main.invokeFramework(Mai  n.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:  280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 4 0 2009-12-12 10:12:17.523
!MESSAGE Application error
!STACK 1
java.lang.NoClassDefFoundError: org/eclipse/core/resources/IContainer
    at org.eclipse.ui.internal.ide.IDEApplication.run(IDE  Application.java:96)
    at org.eclipse.core.internal.runtime.PlatformActivato  r$1.run(PlatformActivator.java:7:cool:
    at org.eclipse.core.runtime.internal.adaptor.EclipseA  ppLauncher.runApplication(EclipseAppLauncher.java:  92)
    at org.eclipse.core.runtime.internal.adaptor.EclipseA  ppLauncher.start(EclipseAppLauncher.java:6:cool:
    at org.eclipse.core.runtime.adaptor.EclipseStarter.ru  n(EclipseStarter.java:400)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.ru  n(EclipseStarter.java:177)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Nativ  e Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Native  MethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(De  legatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.core.launcher.Main.invokeFramework(Mai  n.java:336)
    at org.eclipse.core.launcher.Main.basicRun(Main.java:  280)
    at org.eclipse.core.launcher.Main.run(Main.java:977)
    at org.eclipse.core.launcher.Main.main(Main.java:952)
Caused by: java.lang.ClassNotFoundException: org.eclipse.core.resources.IContainer
    at org.eclipse.osgi.framework.internal.core.BundleLoa  der.findClass(BundleLoader.java:402)
    at org.eclipse.osgi.framework.internal.core.BundleLoa  der.findClass(BundleLoader.java:347)
    at org.eclipse.osgi.internal.baseadaptor.DefaultClass  Loader.loadClass(DefaultClassLoader.java:83)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:2  64)
    at java.lang.ClassLoader.loadClassInternal(ClassLoade  r.java:332)
    ... 14 more

!ENTRY org.eclipse.osgi 2 0 2009-12-12 10:12:17.642
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.ui_1.4.0.20060629124300.jar"]update@../../../home/dan/.eclipse/or...0629124300.jar[/EMAIL] [101] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.visualiser_2.2.0.20060629124300.jar"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.visualiser_2.2.0.20060629 124300.jar[/EMAIL] [102] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.exampl"]update@../../../home/dan/.eclipse/or...se.ajdt.exampl[/EMAIL]es_1.4.0.20060629124300/ [103] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.aspectj.ajde"]update@../../../home/dan/.eclipse/or...g.aspectj.ajde[/EMAIL]_1.5.2.20060629124300/ [105] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.xref.core_1.4.0.20060629124300.jar"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.xref.core_1.4.0.200606291 24300.jar[/EMAIL] [111] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.source"]update@../../../home/dan/.eclipse/or...se.ajdt.source[/EMAIL]_1.4.0.20060629124300/ [113] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.xref.ui_1.4.0.20060629124300.jar"]update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.contribution.xref.ui_1.4.0.20060629124 300.jar[/EMAIL] [115] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-12-12 10:12:17.643
!MESSAGE Bundle [EMAIL="update@../../../home/dan/.eclipse/org.eclipse.sdk.ide/updates/eclipse/plugins/org.eclipse.ajdt.core_1.4.0.20060629124300.jar"]update@../../../home/dan/.eclipse/or...0629124300.jar[/EMAIL] [121] was not resolved.

---

