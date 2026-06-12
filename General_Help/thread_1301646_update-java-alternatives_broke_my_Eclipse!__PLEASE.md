---
title: "update-java-alternatives broke my Eclipse!  PLEASE HELP!!"
date: 2009-10-26
forum: General Help
---

### Post by Shekibobo on 2009-10-26
Yesterday, I ran the following command in order to allow Juniper NetConnect VPN software to run on my computer:

```
sudo update-java-alternatives --plugin--verbose --set ia32-java-6-sun
```

And apparently, this screwed up, at the very least, my Eclipse IDE.  The log gives the following error:

```
!SESSION 2009-10-26 09:42:37.081 -----------------------------------------------
eclipse.buildId=M20090917-0800
java.version=1.6.0_15
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 4 0 2009-10-26 09:42:38.244
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: Cannot load 64-bit SWT libraries on 32-bit JVM
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:179)
    at org.eclipse.swt.internal.Library.loadLibrary(Library.java:159)
    at org.eclipse.swt.internal.C.<clinit>(C.java:21)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:63)
    at org.eclipse.swt.internal.Converter.wcsToMbcs(Converter.java:54)
    at org.eclipse.swt.widgets.Display.<clinit>(Display.java:131)
    at org.eclipse.ui.internal.Workbench.createDisplay(Workbench.java:516)
    at org.eclipse.ui.PlatformUI.createDisplay(PlatformUI.java:161)
    at org.eclipse.ui.internal.ide.application.IDEApplication.createDisplay(IDEApplication.java:143)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:88)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1311)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1287)
```

So, clearly eclipse is trying to run using the 32-bit java.  When I updated java alternatives, did that make it so everything uses 32-bit?  I figured it would just provide an alternative for those programs that were unable to use the 64-bit.  What can I do to fix this problem?

---

### Post by Mighty_Joe on 2009-10-26
> **Shekibobo said:**
> I figured it would just provide an alternative for those programs that were unable to use the 64-bit.  What can I do to fix this problem?

No, update-java-alternatives chooses the system-wide default Java version.  
You can see the installed Java versions using:
```
sudo update-java-alternatives -l 
```

You can set the system-wide default with:
```
sudo update-java-alternatives -s X
```
where X is the version.

---

### Post by Shekibobo on 2009-10-26
So do I need to change my java version whenever I need to use one of these programs?  Or is there possibly some way of bringing ncui libraries over into the java 64-bit (this is the problem for which I need ia32).  Or is there some way of setting the java version for only some of the programs I'm using?

---

### Post by Mighty_Joe on 2009-10-27
When I have an application that requires a specific Java version, I create a "setEnvironment.sh" script that sets the JAVA_HOME and PATH environment variables to that specific version.

---

