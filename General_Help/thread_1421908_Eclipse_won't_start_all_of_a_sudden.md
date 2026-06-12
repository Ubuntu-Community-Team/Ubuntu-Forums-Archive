---
title: "Eclipse won't start all of a sudden"
date: 2010-03-04
forum: General Help
---

### Post by jac0117 on 2010-03-04
My Eclipse just stopped working all of sudden. This happened after I deleted some directories in my workspace, but I doubt that had anything to do with it.

I just get a small empty window when I try to run it. See attached png file

---

### Post by n0dix on 2010-03-04
If you run Eclipse from console do you get any error?

---

### Post by jac0117 on 2010-03-05
I get no errors, but eclipse doesn't even start. I don't get the blank little window anymore. Basically it's not running because I am able to enter more commands on the terminal right after

---

### Post by n0dix on 2010-03-05
> **jac0117 said:**
> I get no errors, but eclipse doesn't even start. I don't get the blank little window anymore. Basically it's not running because I am able to enter more commands on the terminal right after

Are you look if the process is running?

---

### Post by jac0117 on 2010-03-07
The process is running. But all I get is that small empty window. I tried uninstalling and reinstalling it, but I keep getting the same thing.

---

### Post by n0dix on 2010-03-07
1. Disabled visual effects and try again.
2. Try installing manually
2.1 Download Eclipse IDE from the official web page. 
2.2 Extract in /opt folder.
2.3 and run: ./eclipse.

---

### Post by achelis on 2010-03-23
I'm having the same problem.

Thanks for the tips, but unfortunately none of it works. I tried booting in 9.04 and Eclipse runs with no trouble there. I've also tried with both eclipse 3.4 and 3.5 - still no luck.

I've tried "export GDK_NATIVE_WINDOWS=1" but that didn't change anything either.

Eclipse is the last thing I need to get to work to make the switch from 9.04 to 9.10 - any help would be much appreciated :)

---

### Post by cyberkoa on 2010-05-26
I encounter the same problem yesterday, after I setup Android 2.2 SDK development environment, then make an update of android tools. 

After update, I was requested to restart, after restart , I get the same problem.

Start up eclipse at terminal does not show any error message

---

### Post by cyberkoa on 2010-05-26
After start up with -consolelog and -debug params, I got the error message

[HTML]
Starting application: 4850
!SESSION 2010-05-27 10:04:35.076 -----------------------------------------------
eclipse.buildId=M20080911-1700
java.version=1.6.0_18
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86 -consolelog -debug

!ENTRY org.eclipse.ui 2 0 2010-05-27 10:04:41.016
!MESSAGE Warnings while parsing the key bindings from the 'org.eclipse.ui.commands' extension point
!SUBENTRY 1 org.eclipse.ui 2 0 2010-05-27 10:04:41.016
!MESSAGE Cannot bind to an undefined command: plug-in='com.aptana.ide.editors', id='org.eclipse.ui.edit.text.openExternalFile'

!ENTRY org.eclipse.osgi 4 0 2010-05-27 10:04:50.256
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
	at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:1638)
	at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1861)
	at org.eclipse.swt.browser.Browser.setText(Browser.java:737)
	at org.eclipse.jdt.internal.ui.infoviews.JavadocView.doSetInput(JavadocView.java:928)
	at org.eclipse.jdt.internal.ui.infoviews.JavadocView.refresh(JavadocView.java:776)
	at org.eclipse.jdt.internal.ui.infoviews.JavadocView.setBackground(JavadocView.java:763)
	at org.eclipse.jdt.internal.ui.infoviews.AbstractInfoView.inititalizeColors(AbstractInfoView.java:363)
	at org.eclipse.jdt.internal.ui.infoviews.AbstractInfoView.createPartControl(AbstractInfoView.java:226)
	at org.eclipse.ui.internal.ViewReference.createPartHelper(ViewReference.java:371)
	at org.eclipse.ui.internal.ViewReference.createPart(ViewReference.java:230)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:594)
	at org.eclipse.ui.internal.PartPane.setVisible(PartPane.java:306)
	at org.eclipse.ui.internal.ViewPane.setVisible(ViewPane.java:531)
	at org.eclipse.ui.internal.presentations.PresentablePart.setVisible(PresentablePart.java:180)
	at org.eclipse.ui.internal.presentations.util.PresentablePartFolder.select(PresentablePartFolder.java:270)
	at org.eclipse.ui.internal.presentations.util.LeftToRightTabOrder.select(LeftToRightTabOrder.java:65)
	at org.eclipse.ui.internal.presentations.util.TabbedStackPresentation.selectPart(TabbedStackPresentation.java:473)
	at org.eclipse.ui.internal.PartStack.refreshPresentationSelection(PartStack.java:1256)
	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:668)
	at org.eclipse.ui.internal.PartStack.createControl(PartStack.java:576)
	at org.eclipse.ui.internal.PartSashContainer.createControl(PartSashContainer.java:568)
	at org.eclipse.ui.internal.PerspectiveHelper.activate(PerspectiveHelper.java:271)
	at org.eclipse.ui.internal.Perspective.onActivate(Perspective.java:964)
	at org.eclipse.ui.internal.WorkbenchPage.onActivate(WorkbenchPage.java:2593)
	at org.eclipse.ui.internal.WorkbenchWindow$25.run(WorkbenchWindow.java:2873)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
	at org.eclipse.ui.internal.WorkbenchWindow.setActivePage(WorkbenchWindow.java:2854)
	at org.eclipse.ui.internal.WorkbenchWindow$19.runWithException(WorkbenchWindow.java:2171)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$27.runWithException(Workbench.java:1361)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2293)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2198)
	at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:493)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:288)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:488)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:113)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:193)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:386)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:179)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

[/HTML]

---

### Post by adamnfish on 2010-07-24
I appear to be having the same problem. I recently updated this machine to Ubuntu 10.04 (which involved a few upgrades - I was a bit behind!). I'm fairly sure Eclipse was working OK after this process (I think I've used it on this machine since then).

More recently, I installed version 2.2 of the Android SDK to root my N1. (I installed it 'standalone' because I just wanted to use ADB)

Today, I have opened up Eclipse (which worked fine) but upon switching away from my Python workspace (I use PyDev, PDT and the Android SDK) to a new workspace (which obviously triggers a restart) all subsequent attempts to start eclipse are failing - I just see a blank dialogue box as described above. This dialogue box cannot be closed, I have to kill the process to get id of it. Starting Eclipse with -consolelog and -debug from the terminal gives me the following output:

```

/usr/local/eclipse/eclipse -consolelog -debug
Start VM: -Xms40m
-Xmx256m
-XX:MaxPermSize=256m
-Djava.class.path=/usr/local/eclipse//plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar
-os linux
-ws gtk
-arch x86
-showsplash /usr/local/eclipse//plugins/org.eclipse.platform_3.3.101.v200902111700/splash.bmp
-launcher /usr/local/eclipse/eclipse
-name Eclipse
--launcher.library /usr/local/eclipse/plugins/org.eclipse.equinox.launcher.gtk.linux.x86_1.0.101.R34x_v20080805/eclipse_1115.so
-startup /usr/local/eclipse//plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar
-consolelog
-debug
-vm /usr/lib/jvm/java-6-openjdk/jre/bin/../lib/i386/client/libjvm.so
-vmargs
-Xms40m
-Xmx256m
-XX:MaxPermSize=256m
-Djava.class.path=/usr/local/eclipse//plugins/org.eclipse.equinox.launcher_1.0.101.R34x_v20081125.jar 
Install location:
    file:/usr/local/eclipse/
Configuration file:
    file:/usr/local/eclipse/configuration/config.ini loaded
Configuration location:
    file:/usr/local/eclipse/configuration/
Framework located:
    file:/usr/local/eclipse/plugins/org.eclipse.osgi_3.4.3.R34x_v20081215-1030.jar
Framework classpath:
    file:/usr/local/eclipse/plugins/org.eclipse.osgi_3.4.3.R34x_v20081215-1030.jar
Splash location:
    /usr/local/eclipse//plugins/org.eclipse.platform_3.3.101.v200902111700/splash.bmp
Debug options:
    file:/home/adamnfish/.options not found
Time to load bundles: 4
Starting application: 649
!SESSION 2010-07-24 14:09:11.507 -----------------------------------------------
eclipse.buildId=M20090211-1700
java.version=1.6.0_18
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86 -consolelog -debug

!ENTRY org.eclipse.ui.workbench 4 0 2010-07-24 14:09:16.423
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
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
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2010-07-24 14:09:16.426
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
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
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2010-07-24 14:09:16.428
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
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
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.ui.workbench 4 0 2010-07-24 14:09:16.429
!MESSAGE Widget disposed too early!
!STACK 0
java.lang.RuntimeException: Widget disposed too early!
	at org.eclipse.ui.internal.WorkbenchPartReference$1.widgetDisposed(WorkbenchPartReference.java:171)
	at org.eclipse.swt.widgets.TypedListener.handleEvent(TypedListener.java:117)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1158)
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
	at org.eclipse.swt.widgets.Shell.releaseChildren(Shell.java:1948)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)

!ENTRY org.eclipse.osgi 4 0 2010-07-24 14:09:16.449
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
	at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:1638)
	at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1861)
	at org.eclipse.swt.browser.Browser.setText(Browser.java:737)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.generateContentForPage(BrowserIntroPartImplementation.java:252)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.dynamicStandbyStateChanged(BrowserIntroPartImplementation.java:451)
	at org.eclipse.ui.internal.intro.impl.presentations.BrowserIntroPartImplementation.doStandbyStateChanged(BrowserIntroPartImplementation.java:658)
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
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3036)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:803)
	at org.eclipse.ui.internal.Workbench$27.runWithException(Workbench.java:1363)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:133)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3378)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:549)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:504)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1236)


```

Any assistance would be very much appreciated, I've really no idea how to proceed from here beyond trying to remove and re-install Eclipse from scratch.

---

### Post by ilganeli on 2010-09-09
After updating to the most recent version of Ubuntu I am having the same problems. Has anyone found a fix to this?

---

### Post by achelis on 2010-09-09
After changing to Eclipse Helios I haven't had problems with Eclipse on 10.4. I'm downloading from the eclipse download site - so not using apt-get. And I'm using the sun-java6 package.

---

### Post by vivace on 2010-09-13
This started happening to me. 

I wonder if its because my java version may have changed?? :

java -version
java version "1.6.0_20"
Java(TM) SE Runtime Environment (build 1.6.0_20-b02)
Java HotSpot(TM) Server VM (build 16.3-b01, mixed mode)

---

### Post by michi_h57 on 2010-09-13
maybe some 32-bit vs 64-bit issue? (was the case for me)

---

### Post by vivace on 2010-09-14
hmm yea thats a possibility--i mean it makes sense since i think i may have installed some kind of 32 bit plugin. Do you know how i can fix it?? sorry im a complete noob.

---

### Post by crafter on 2010-09-19
I'm having the same problem. From what I gathered from other information gained from searching the 'net, the problem might be related to XULRunner updates. I do recall that my last update included XULRunner.

I don't have a solution, but perhaps this info might steer someone toward one.

---

### Post by crafter on 2010-09-19
I removed xulrunner as suggested here [https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/583552]("https://bugs.launchpad.net/ubuntu/+source/eclipse/+bug/583552") and here [http://www.dataforte.net/blog/2010/03/03/eclipse-crashes-with-lucid/]("http://www.dataforte.net/blog/2010/03/03/eclipse-crashes-with-lucid/") but that did not work for me.

Luckily I still had the galileo install and starting that gave me an error message about an error in the log file **/home/me/workspace/.metadata/.log**.

I cleared the log file and then restarted Helios. Looking through the log file pointed to an empty file in /home/me/workspace/.metadata/.plugins/org.eclipse.core.resources/.root/

```
Root exception:
org.eclipse.core.internal.resources.ResourceException(/home/pradesh/workspace/.metadata/.plugins/org.eclipse.core.resources/.root/28.tree)[567]: java.io.EOFException
        at java.io.DataInputStream.readInt(DataInputStream.java:375)

```

Since the file was empty I deleted it and restarted it. Helios restarted it but with two slight problems:-
1. The window decoration looks "plain".
2. My project entries don't show up in the workbench.

My problem may not be the same as yours, but at least look in the 
**/home/me/workspace/.metadata/.log** file for a clue.

Good luck

---

### Post by jac0117 on 2010-11-09
> **n0dix said:**
> 1. Disabled visual effects and try again.
2. Try installing manually
2.1 Download Eclipse IDE from the official web page. 
2.2 Extract in /opt folder.
2.3 and run: ./eclipse.

--------------
I'm revisiting this issue after a long time. I had been using Netbeans during this time. I was surprised to find my own thread as the first result in google. Anyway, if anyone is still having this problem, the solution above worked for me.

---

### Post by toddmallen on 2010-12-03
I encountered the same problem after upgrading to 10.10 (and  uninstalling/reinstalling Eclipse as that's usually required after a  Ubuntu version upgrade to get it to play nicely with CDT), and  unfortunately can find nothing that works for it. I've found Google  threads that suggest using eclipse -clean, temporarily moving the  ~/workbench and ~/.eclipse directories during the initial startup, doing  a complete removal/reinstall, uninstalling/reinstalling xulrunner, and  similar ones to those here such as removing certain entries in  ~/workspace/.metadata.

None of those suggestions have worked, and  I can't find any more. I also tried tweaking the config in .eclipse to  use the main path (/usr/lib/eclipse) rather than just plugins/..., but  no dice there either. Only a direct download from the Eclipse website  worked, and that of course does not allow Synaptic/apt to control the  upgrades. For the moment, it's what there is, though.

Has anyone had any luck in clearing this up? Everything above that I tried just results in the same error.

---

### Post by dgrafix on 2011-02-22
I have now got same problem (Ubu 10.4 64)
This thread has been marked solved, but what is the solution?
Or did i miss it? :D

Edit oh i see no that did not work for me either

I am going to have to go back to old ubuntu or use windoze <:( until this is resolved. 
Unfortunately i cannot use netbeans (afaik anyway, it does not allow libs to be declared in android projects... or so it would seem)

---

### Post by dgrafix on 2011-02-23
Ok i solved it.

It was using the 32 bit javavm

I removed all sun java stuff and reinstalled it. Then installed eclipse, works now.

---

### Post by esod on 2011-04-02
Deleting the workspace folder got eclipse running again for me. That wasn't a problem since I wasn't using the workspace folder for anything. Unfortunately I now have to reset Preferences and rebuild Projects, which is a bit of a drag. 

I attribute the issue to my lack of knowledge since I just started using eclipse. At least I don't have to dismantle anything deeper.

---

### Post by philescandon on 2012-02-05
Eclipse became unresponsive while saving a workspace (using the epic perl editor plugin) - anyhow, couldn't boot eclipse afterwards.

Tried everything mentioned above, but what worked for me is changing my java version open jdk to sun.
Terminal window:
sudo update-alternatives --config java
Changed to sun... eclipse now boots.

---

### Post by punkr0csux on 2012-07-26
> **esod said:**
> Deleting the workspace folder got eclipse running again for me.


This worked for me as well. Thanks.

---

