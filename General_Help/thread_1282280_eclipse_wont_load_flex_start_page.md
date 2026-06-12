---
title: "eclipse wont load flex start page?"
date: 2009-10-04
forum: General Help
---

### Post by abhilashm86 on 2009-10-04
i installed flex builder in eclipse, it works fine, but i'm unable to access flex start page under help, which gives reference and help instantly........
this is error given by it, how to solve?
```
java.lang.NullPointerException
	at com.adobe.flexbuilder.ui.StartPage.createPartControl(StartPage.java:48)
	at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:661)
	at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:426)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:592)
	at org.eclipse.ui.internal.EditorAreaHelper.setVisibleEditor(EditorAreaHelper.java:263)
	at org.eclipse.ui.internal.EditorManager.setVisibleEditor(EditorManager.java:1405)
	at org.eclipse.ui.internal.EditorManager$5.runWithException(EditorManager.java:939)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:129)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3296)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2974)
	at org.eclipse.ui.application.WorkbenchAdvisor.openWindows(WorkbenchAdvisor.java:801)
	at org.eclipse.ui.internal.Workbench$25.runWithException(Workbench.java:1342)
	at org.eclipse.ui.internal.StartupThreading$StartupRunnable.run(StartupThreading.java:31)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:129)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3296)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2974)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2309)
	at org.eclipse.ui.internal.Workbench.access$4(Workbench.java:2219)
	at org.eclipse.ui.internal.Workbench$4.run(Workbench.java:466)
	at org.eclipse.core.databinding.observable.Realm.runWithDefault(Realm.java:289)
	at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Workbench.java:461)
	at org.eclipse.ui.PlatformUI.createAndRunWorkbench(PlatformUI.java:149)
	at org.eclipse.ui.internal.ide.application.IDEApplication.start(IDEApplication.java:106)
	at org.eclipse.equinox.internal.app.EclipseAppHandle.run(EclipseAppHandle.java:169)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(EclipseAppLauncher.java:106)
	at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(EclipseAppLauncher.java:76)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:363)
	at org.eclipse.core.runtime.adaptor.EclipseStarter.run(EclipseStarter.java:176)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:508)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:447)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1173)

```

---

### Post by abhilashm86 on 2009-10-04
bump!! any help??

---

