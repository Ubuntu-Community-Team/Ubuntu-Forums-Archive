---
title: "eclipse stopped working correctly all of the sudden"
date: 2012-09-14
forum: General Help
---

### Post by eantoranz on 2012-09-14
Hi!

I've been using eclipse 4.2 (not from packages) without a single hiccup for months already. Now, all of the sudden, eclipse started to misbehave. Can't go into some of the config frames. If I go into configuration->Java->Debug, I see an error like this:

```

Unable to create the selected preference page

An error occurred while automatically activating
bundle org.eclipse.jdt.debug.ui (146).

```

I'm using openJDK as my JDK:

```

$ which java
/usr/bin/java
$ java -version
java version "1.6.0_24"
OpenJDK Runtime Environment (IcedTea6 1.11.4) (6b24-1.11.4-1ubuntu0.12.04.1)
OpenJDK Server VM (build 20.0-b12, mixed mode)

```

I just tried chaning my java home to use jdk 1.5 from oracle but it made no change at all:

```

$ export JAVA_HOME=~/Descargas/java/jdk1.5.0_22/
$ ~/Descargas/eclipse/eclipse/eclipse

```

I even created a whole new user and started eclipse from there with the same results. This last tip makes me think that there was probably a software upgrade yesterday that broke this thing. You have any idea what's going on? Do you have any idea how I could get verbose output from eclipse about what's going on? I tried running with --debug, also with --clean, also added -Xdebug to eclipse.ini.... none of them did anything.

Thanks in advance.

---

### Post by eantoranz on 2012-09-14
I found this:

```

!ENTRY org.eclipse.equinox.registry 4 1 2012-09-14 09:27:06.537
!MESSAGE Unable to create the selected preference page.
!STACK 0
org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter$TerminatingClassNotFoundException: An error occurred while automatically activating bundle org.eclipse.jdt.debug.ui (146).
        at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:122)
        at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:469)
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:216)
        at org.eclipse.osgi.internal.loader.BundleLoader.findLocalClass(BundleLoader.java:395)
        at org.eclipse.osgi.internal.loader.BundleLoader.findClassInternal(BundleLoader.java:464)
        at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:421)
        at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:412)
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:107)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
        at org.eclipse.osgi.internal.loader.BundleLoader.loadClass(BundleLoader.java:340)
        at org.eclipse.osgi.framework.internal.core.BundleHost.loadClass(BundleHost.java:229)
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadClass(AbstractBundle.java:1212)
        at org.eclipse.core.internal.registry.osgi.RegistryStrategyOSGI.createExecutableExtension(RegistryStrategyOSGI.java:174)
        at org.eclipse.core.internal.registry.ExtensionRegistry.createExecutableExtension(ExtensionRegistry.java:905)
        at org.eclipse.core.internal.registry.ConfigurationElement.createExecutableExtension(ConfigurationElement.java:243)
        at org.eclipse.core.internal.registry.ConfigurationElementHandle.createExecutableExtension(ConfigurationElementHandle.java:55)
        at org.eclipse.ui.internal.WorkbenchPlugin$1.run(WorkbenchPlugin.java:273)
        at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
        at org.eclipse.ui.internal.WorkbenchPlugin.createExtension(WorkbenchPlugin.java:269)
        at org.eclipse.ui.internal.dialogs.WorkbenchPreferenceNode.createPage(WorkbenchPreferenceNode.java:47)
        at org.eclipse.jface.preference.PreferenceDialog.createPage(PreferenceDialog.java:1340)
        at org.eclipse.ui.internal.dialogs.FilteredPreferenceDialog.createPage(FilteredPreferenceDialog.java:377)
        at org.eclipse.jface.preference.PreferenceDialog.showPage(PreferenceDialog.java:1231)
        at org.eclipse.ui.internal.dialogs.FilteredPreferenceDialog.showPage(FilteredPreferenceDialog.java:675)
        at org.eclipse.jface.preference.PreferenceDialog$10.run(PreferenceDialog.java:709)
        at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
        at org.eclipse.jface.preference.PreferenceDialog$9.selectionChanged(PreferenceDialog.java:705)
        at org.eclipse.jface.viewers.StructuredViewer$3.run(StructuredViewer.java:888)
        at org.eclipse.core.runtime.SafeRunner.run(SafeRunner.java:42)
        at org.eclipse.ui.internal.JFaceUtil$1.run(JFaceUtil.java:49)
        at org.eclipse.jface.util.SafeRunnable.run(SafeRunnable.java:175)
        at org.eclipse.jface.viewers.StructuredViewer.firePostSelectionChanged(StructuredViewer.java:886)
        at org.eclipse.jface.viewers.StructuredViewer.handlePostSelect(StructuredViewer.java:1226)
        at org.eclipse.jface.viewers.StructuredViewer$5.widgetSelected(StructuredViewer.java:1251)
        at org.eclipse.jface.util.OpenStrategy.firePostSelectionEvent(OpenStrategy.java:262)
        at org.eclipse.jface.util.OpenStrategy.access$5(OpenStrategy.java:256)
        at org.eclipse.jface.util.OpenStrategy$3.run(OpenStrategy.java:433)
        at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
        at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:135)
        at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3529)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3182)
        at org.eclipse.jface.window.Window.runEventLoop(Window.java:825)
        at org.eclipse.jface.window.Window.open(Window.java:801)
        at org.eclipse.ui.internal.dialogs.WorkbenchPreferenceDialog.open(WorkbenchPreferenceDialog.java:215)
        at org.eclipse.ui.internal.OpenPreferencesAction.run(OpenPreferencesAction.java:65)
        at org.eclipse.jface.action.Action.runWithEvent(Action.java:498)
        at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:584)
        at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:501)
        at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:411)
        at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
        at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1276)
        at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3554)
        at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3179)
        at org.eclipse.e4.ui.internal.workbench.swt.PartRenderingEngine$9.run(PartRenderingEngine.java:1022)
        at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
        at org.eclipse.e4.ui.internal.workbench.swt.PartRenderingEngine.run(PartRenderingEngine.java:916)
        at org.eclipse.e4.ui.internal.workbench.E4Workbench.createAndRunUI(E4Workbench.java:86)
        at org.eclipse.ui.internal.Workbench$5.run(Workbench.java:585)
        at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:332)
        at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:540)
        at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
        at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:124)
        at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:196)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:110)
        at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:79)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:353)
        at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:180)
        at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
        at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
        at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
        at java.lang.reflect.Method.invoke(Method.java:616)
        at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:629)
        at org.eclipse.equinox.launcher.Main.basicRun(Main.java:584)
        at org.eclipse.equinox.launcher.Main.run(Main.java:1438)
Caused by: org.osgi.framework.BundleException: The activator org.eclipse.jdt.internal.debug.ui.JDIDebugUIPlugin for bundle org.eclipse.jdt.debug.ui is invalid
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:172)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:679)
        at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:381)
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:300)
        at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:440)
        at org.eclipse.osgi.internal.loader.BundleLoader.setLazyTrigger(BundleLoader.java:263)
        at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:107)
        ... 73 more
Caused by: java.lang.NoClassDefFoundError: org/eclipse/jdt/debug/core/IJavaHotCodeReplaceListener
        at java.lang.Class.getDeclaredConstructors0(Native Method)
        at java.lang.Class.privateGetDeclaredConstructors(Class.java:2406)
        at java.lang.Class.getConstructor0(Class.java:2716)
        at java.lang.Class.newInstance0(Class.java:343)
        at java.lang.Class.newInstance(Class.java:325)
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.loadBundleActivator(AbstractBundle.java:167)
        ... 79 more
Caused by: org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter$TerminatingClassNotFoundException: An error occurred while automatically activating bundle org.eclipse.jdt.debug (145).
        at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:122)
        at org.eclipse.osgi.baseadaptor.loader.ClasspathManager.findLocalClass(ClasspathManager.java:469)
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.findLocalClass(DefaultClassLoader.java:216)
        at org.eclipse.osgi.internal.loader.BundleLoader.findLocalClass(BundleLoader.java:395)
        at org.eclipse.osgi.internal.loader.SingleSourcePackage.loadClass(SingleSourcePackage.java:35)
        at org.eclipse.osgi.internal.loader.BundleLoader.findClassInternal(BundleLoader.java:461)
        at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:421)
        at org.eclipse.osgi.internal.loader.BundleLoader.findClass(BundleLoader.java:412)
        at org.eclipse.osgi.internal.baseadaptor.DefaultClassLoader.loadClass(DefaultClassLoader.java:107)
        at java.lang.ClassLoader.loadClass(ClassLoader.java:266)
        ... 85 more
Caused by: org.osgi.framework.BundleException: Exception in org.eclipse.jdt.internal.debug.core.JDIDebugPlugin.start() of bundle org.eclipse.jdt.debug.
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:734)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.start(BundleContextImpl.java:683)
        at org.eclipse.osgi.framework.internal.core.BundleHost.startWorker(BundleHost.java:381)
        at org.eclipse.osgi.framework.internal.core.AbstractBundle.start(AbstractBundle.java:300)
        at org.eclipse.osgi.framework.util.SecureAction.start(SecureAction.java:440)
        at org.eclipse.osgi.internal.loader.BundleLoader.setLazyTrigger(BundleLoader.java:263)
        at org.eclipse.core.runtime.internal.adaptor.EclipseLazyStarter.postFindLocalClass(EclipseLazyStarter.java:107)
        ... 94 more
Caused by: java.lang.NoClassDefFoundError: Could not initialize class com.ibm.icu.text.SimpleDateFormat
        at org.eclipse.jdt.internal.debug.core.JDIDebugOptions.<clinit>(JDIDebugOptions.java:58)
        at org.eclipse.jdt.internal.debug.core.JDIDebugPlugin.start(JDIDebugPlugin.java:274)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl$1.run(BundleContextImpl.java:711)
        at java.security.AccessController.doPrivileged(Native Method)
        at org.eclipse.osgi.framework.internal.core.BundleContextImpl.startActivator(BundleContextImpl.java:702)
        ... 100 more

```

Any idea what's going on?

---

### Post by eantoranz on 2012-09-14
With a tip from [http://stackoverflow.com/questions/1553343/cannot-run-debug-java-applications-in-eclipse-javatimezone-issue](http://stackoverflow.com/questions/1553343/cannot-run-debug-java-applications-in-eclipse-javatimezone-issue), I added this to eclipse.ini:

```

-Dcom.ibm.icu.util.TimeZone.DefaultTimeZoneType=ICU

```

That solved it.

---

