---
title: "Problems with Eclipse 3.4.0 on Unbuntu 9.10"
date: 2009-11-11
forum: General Help
---

### Post by Soria Max on 2009-11-11
I have a problem with Eclipse 3.4.2 in Ubuntu 9.10 which does not allow me elcipse up and tells me see the file / workspace / .metadata / .log this is the message:
!SESSION 2009-11-11 12:04:24.520 -----------------------------------------------
eclipse.buildId=M20090211-1700
java.version=1.6.0_15
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=es_BO
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.ui.workbench 4 0 2009-11-11 12:05:02.286
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
    at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
    at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:115
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
    at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
    at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:194
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
    at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
    at org.eclipse.swt.widgets.Display.release(Display.java:3083)
    at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-11-11 12:05:02.346
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
    at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
    at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:115
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
    at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
    at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:194
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
    at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
    at org.eclipse.swt.widgets.Display.release(Display.java:3083)
    at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-11-11 12:05:02.350
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
    at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
    at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:115
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
    at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
    at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:194
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
    at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
    at org.eclipse.swt.widgets.Display.release(Display.java:3083)
    at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2009-11-11 12:05:02.358
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
    at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
    at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:115
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1182)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1163)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1026)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Composite.releaseChildren(Composite.java:1184)
    at org.eclipse.swt.widgets.Canvas.releaseChildren(Canvas.java:211)
    at org.eclipse.swt.widgets.Decorations.releaseChildren(Decorations.java:466)
    at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:194
    at org.eclipse.swt.widgets.Widget.release(Widget.java:1029)
    at org.eclipse.swt.widgets.Control.release(Control.java:3221)
    at org.eclipse.swt.widgets.Widget.dispose(Widget.java:442)
    at org.eclipse.swt.widgets.Shell.dispose(Shell.java:1893)
    at org.eclipse.swt.widgets.Display.release(Display.java:3083)
    at org.eclipse.swt.graphics.Device.dispose(Device.java:237)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:129)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2009-11-11 12:05:02.497
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
    at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:163
    at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1861)
    at org.eclipse.swt.browser.Browser.setText(Browser.java:737)
    at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateContentForPage(BrowserIntroPartImplementation.java:252)
    at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(BrowserIntroPartImplementation.java:451)
    at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged(BrowserIntroPartImplementation.java:65
    at org.eclipse.ui.internal.intro.impl.model.AbstractIntroPartImplementation.standbyStateChanged(AbstractIntroPartImplementation.java:249)
    at org.eclipse.ui.internal.intro.impl.model.IntroPartPresentation.standbyStateChanged(IntroPartPresentation.java:443)
    at org.eclipse.ui.intro.config.CustomizableIntroPart.standbyStateChanged(CustomizableIntroPart.java:266)
    at org.eclipse.ui.internal.ViewIntroAdapterPart$2.run(ViewIntroAdapterPart.java:74)
    at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
    at org.eclipse.ui.internal.ViewIntroAdapterPart.setStandby(ViewIntroAdapterPart.java:70)
    at org.eclipse.ui.internal.ViewIntroAdapterPart$1.propertyChanged(ViewIntroAdapterPart.java:55)
    at org.eclipse.ui.internal.WorkbenchPartReference.fireInternalPropertyChange(WorkbenchPartReference.java:374)
    at org.eclipse.ui.internal.WorkbenchPartReference.fireZoomChange(WorkbenchPartReference.java:539)
    at org.eclipse.ui.internal.PartPane.setZoomed(PartPane.java:349)
    at org.eclipse.ui.internal.PartStack.setZoomed(PartStack.java:1526)
    at org.eclipse.ui.internal.PartSashContainer.zoomIn(PartSashContainer.java:884)
    at org.eclipse.ui.internal.PartSashContainer.childRequestZoomIn(PartSashContainer.java:905)
    at org.eclipse.ui.internal.LayoutPart.requestZoomIn(LayoutPart.java:354)
    at org.eclipse.ui.internal.PartStack.setState(PartStack.java:1501)
    at org.eclipse.ui.internal.WorkbenchPage.setState(WorkbenchPage.java:3872)
    at org.eclipse.ui.internal.WorkbenchPage.toggleZoom(WorkbenchPage.java:3944)
    at org.eclipse.ui.internal.WorkbenchIntroManager.setIntroStandby(WorkbenchIntroManager.java:201)
    at org.eclipse.ui.internal.WorkbenchIntroManager.showIntro(WorkbenchIntroManager.java:136)
    at org.eclipse.ui.application.WorkbenchWindowAdvisor.openIntro(WorkbenchWindowAdvisor.java:173)
    at org.eclipse.ui.internal.ide.application.IDEWorkbenchWindowAdvisor.openIntro(IDEWorkbenchWindowAdvisor.java:458)
    at org.eclipse.ui.internal.WorkbenchWindow.open(WorkbenchWindow.java:777)
    at org.eclipse.ui.internal.Workbench$22.runWithException(Workbench.java:1043)
    at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:337
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
    at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
    at org.eclipse.ui.internal.Workbench$27.runWithException(Workbench.java:1363)
    at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
    at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:337
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
    at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2295)
    at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2200)
    at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:495)
    at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:288)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:490)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
    at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
    at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
    at java.lang.reflect.Method.invoke(Method.java:597)
    at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
    at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
    at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

and not to do please help.

---

### Post by andrewc6l on 2009-11-11
Try running (from the command line) eclipse -clean instead of just eclipse.

---

### Post by tfmorris on 2009-11-19
You are probably running into this bug [https://bugs.eclipse.org/bugs/show_bug.cgi?id=268651](https://bugs.eclipse.org/bugs/show_bug.cgi?id=268651)

Since there's no Eclipse 3.4.3, you'll need to update to Eclipse 3.5 if possible.

You may be able to work around the startup crash by putting

  showIntro=false

in the file

  <eclipse>/workspace/.metadata/.plugins/org.eclipse.core.runtime/.settings


But you'll likely have problems anywhere else it tries to use Mozilla.

---

### Post by datajack on 2010-01-19
I have a fix! (I think)

As has been noted, this is due to an incompatibility with the installed version of xulrunner. The fix is to install xulrunner 1.8 (the easy bit) and getting eclipse to actually use it (what I've spent the last hour banging my head trying to do). Anyways...

Install xulruner 1.8 :

```
apt-get install xulrunner
```

You will want to create a shell script launcher for eclipse. Here's mine, it deals with the button click problems as well as the xulrunner problem :

```

#/bin/sh

export GDK_NATIVE_WINDOWS=1
/opt/eclipse/eclipse.real -vmargs -Dorg.eclipse.swt.browser.XULRunnerPath=/usr/lib/xulrunner/xulrunner

```

Note that I have renamed the original eclipse binary to eclipse.real

Works for me :)

---

### Post by glorge on 2010-03-10
Thank you datajack for the quick and easy fix!

---

