---
title: "Eclipse Error"
date: 2011-05-09
forum: General Help
---

### Post by cesiel1990 on 2011-05-09
I had eclipse running on 10.10.  I upgraded to 11.04 and when I try running it I get: 

An error has occurred.  See the log file
/home/dcesiel/.eclipse/org.eclipse.platform_3.5.0_155965261/configuration/1304988081506.log

Here is the log:

```
!SESSION 2011-05-09 20:40:54.580 -----------------------------------------------
eclipse.buildId=M20100211-1343
java.version=1.6.0_22
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2011-05-09 20:40:54.864
!MESSAGE 
!STACK 0
org.osgi.framework.BundleException: Exception in org.eclipse.osgi.framework.internal.core.SystemBundleActivator.start() of bundle org.eclipse.osgi.
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:806)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:755)
	at org.eclipse.osgi.framework.internal.core.InternalSystemBundle.resume(InternalSystemBundle.java:207)
	at org.eclipse.osgi.framework.internal.core.Framework.launch(Framework.java:649)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:298)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:175)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)
Caused by: java.lang.NullPointerException
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.setExportPackages(BundleDescriptionImpl.java:258)
	at org.eclipse.osgi.internal.resolver.StateReader.readBundleDescriptionLazyData(StateReader.java:268)
	at org.eclipse.osgi.internal.resolver.StateReader.fullyLoad(StateReader.java:688)
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.loadLazyData(BundleDescriptionImpl.java:570)
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.getExportPackages(BundleDescriptionImpl.java:140)
	at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.setFrameworkVersion(PackageAdminImpl.java:695)
	at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.setResolvedBundles(PackageAdminImpl.java:645)
	at org.eclipse.osgi.framework.internal.core.SystemBundleActivator.start(SystemBundleActivator.java:65)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:783)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:774)
	... 12 more
Root exception:
java.lang.NullPointerException
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.setExportPackages(BundleDescriptionImpl.java:258)
	at org.eclipse.osgi.internal.resolver.StateReader.readBundleDescriptionLazyData(StateReader.java:268)
	at org.eclipse.osgi.internal.resolver.StateReader.fullyLoad(StateReader.java:688)
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.loadLazyData(BundleDescriptionImpl.java:570)
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.getExportPackages(BundleDescriptionImpl.java:140)
	at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.setFrameworkVersion(PackageAdminImpl.java:695)
	at org.eclipse.osgi.framework.internal.core.PackageAdminImpl.setResolvedBundles(PackageAdminImpl.java:645)
	at org.eclipse.osgi.framework.internal.core.SystemBundleActivator.start(SystemBundleActivator.java:65)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:783)
	at java.security.AccessController.doPrivileged(Native Method)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:774)
	at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:755)
	at org.eclipse.osgi.framework.internal.core.InternalSystemBundle.resume(InternalSystemBundle.java:207)
	at org.eclipse.osgi.framework.internal.core.Framework.launch(Framework.java:649)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:298)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:175)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)

!ENTRY org.eclipse.osgi 4 0 2011-05-09 20:40:54.869
!MESSAGE Startup error
!STACK 1
java.lang.RuntimeException: Exception in org.eclipse.osgi.framework.internal.core.SystemBundleActivator.start() of bundle org.eclipse.osgi.
	at org.eclipse.osgi.framework.internal.core.InternalSystemBundle.resume(InternalSystemBundle.java:215)
	at org.eclipse.osgi.framework.internal.core.Framework.launch(Framework.java:649)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.startup(EclipseStarter.java:298)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:175)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)
!SESSION Mon May 09 20:40:54 EDT 2011 ------------------------------------------
!ENTRY org.eclipse.equinox.launcher 4 0 2011-05-09 20:40:54.881
!MESSAGE Exception launching the Eclipse Platform:
!STACK
java.lang.NullPointerException
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.setExportPackages(BundleDescriptionImpl.java:258)
	at org.eclipse.osgi.internal.resolver.StateReader.readBundleDescriptionLazyData(StateReader.java:268)
	at org.eclipse.osgi.internal.resolver.StateReader.fullyLoad(StateReader.java:688)
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.loadLazyData(BundleDescriptionImpl.java:570)
	at org.eclipse.osgi.internal.resolver.BundleDescriptionImpl.getExportPackages(BundleDescriptionImpl.java:140)
	at org.eclipse.osgi.internal.resolver.StateHelperImpl.getExportedPackageMap(StateHelperImpl.java:74)
	at org.eclipse.osgi.internal.resolver.StateHelperImpl.getUnsatisfiedLeaves(StateHelperImpl.java:109)
	at org.eclipse.osgi.internal.resolver.StateHelperImpl.getUnsatisfiedLeaves(StateHelperImpl.java:154)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.logUnresolvedBundles(EclipseStarter.java:448)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:189)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)

```

Any idea how I can fix this?

---

