---
title: "Eclipse 3.5 not working at all"
date: 2010-04-07
forum: General Help
---

### Post by Ciarán McCann on 2010-04-07
Hi all 

I install eclipse via the synaptic package manager and it did work before but I was messing around with some svn packages and corrupted it. So naturally I did a complete removal of anything related to eclipse and reinstalled all the packages after, but to no avail problem still persists. here is the log file it tells me to look at, can really make head or tales of this stack error info, not really a big Java man.

I have a 64bit install of ubuntu 9.10

> 
!SESSION 2010-04-08 00:56:19.723 -----------------------------------------------
eclipse.buildId=M20090917-0800
java.version=1.6.0_0
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86_64, WS=gtk, NL=en_IE
Command-line arguments:  -os linux -ws gtk -arch x86_64

!ENTRY org.eclipse.osgi 4 0 2010-04-08 00:56:22.428
!MESSAGE Application error
!STACK 1
java.lang.UnsatisfiedLinkError: org.eclipse.swt.internal.gtk.OS._gdk_window_restack(JJZ)V
    at org.eclipse.swt.internal.gtk.OS._gdk_window_restack(Native Method)
    at org.eclipse.swt.internal.gtk.OS.gdk_window_restack(OS.java:4900)
    at org.eclipse.swt.widgets.Control.restackWindow(Control.java:3337)
    at org.eclipse.swt.widgets.Control.setZOrder(Control.java:4192)
    at org.eclipse.swt.widgets.Control.setZOrder(Control.java:4130)
    at org.eclipse.swt.widgets.Control.moveAbove(Control.java:1091)
    at org.eclipse.jface.action.StatusLine$StatusLineLayout.layout(StatusLine.java:175)
    at org.eclipse.swt.widgets.Composite.updateLayout(Composite.java:1428)
    at org.eclipse.swt.widgets.Composite.layout(Composite.java:920)
    at org.eclipse.swt.widgets.Composite.layout(Composite.java:878)
    at org.eclipse.swt.widgets.Composite.layout(Composite.java:841)
    at org.eclipse.jface.action.StatusLineManager.update(StatusLineManager.java:340)
    at org.eclipse.jface.action.StatusLineManager.createControl(StatusLineManager.java:100)
    at org.eclipse.ui.presentations.AbstractPresentationFactory.createStatusLineControl(AbstractPresentationFactory.java:125)
    at org.eclipse.ui.internal.WorkbenchWindow.createStatusLine(WorkbenchWindow.java:3906)
    at org.eclipse.ui.internal.WorkbenchWindow.createDefaultContents(WorkbenchWindow.java:1084)
    at org.eclipse.ui.internal.WorkbenchWindowConfigurer.createDefaultContents(WorkbenchWindowConfigurer.java:625)
    at org.eclipse.ui.application.WorkbenchWindowAdvisor.createWindowContents(WorkbenchWindowAdvisor.java:268)
    at org.eclipse.ui.internal.WorkbenchWindow.createContents(WorkbenchWindow.java:1000)
    at org.eclipse.jface.window.Window.create(Window.java:431)
    at org.eclipse.ui.internal.Workbench$20.runWithException(Workbench.java:1032)
    at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:134)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3468)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3115)
    at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
    at org.eclipse.ui.internal.Workbench$28.runWithException(Workbench.java:1384)
    at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:134)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3468)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3115)
    at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2316)
    at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2221)
    at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:500)
    at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:493)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:194)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:368)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
    at java.lang.reflect.Method.invoke(Method.java:616)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1311)
    at org.eclipse.equinox.launcher.Main.main(Main.java:1287)



---

### Post by Ciarán McCann on 2010-04-07
Just found the solution here
[http://ubuntuforums.org/archive/index.php/t-1287461.html](http://ubuntuforums.org/archive/index.php/t-1287461.html)

---

