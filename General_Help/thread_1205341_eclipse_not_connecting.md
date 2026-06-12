---
title: "eclipse not connecting??"
date: 2009-07-05
forum: General Help
---

### Post by abhilashm86 on 2009-07-05
i installed europa, also i installed flex plugin but flex start page and webpage is not opening, during installation it gave error like, you have another flash player already check........
what i need to do now,
also this is error, 
```
java.lang.NullPointerException
	at com.adobe.flexbuilder.ui.StartPage.createPartControl(StartPage.java:48)
	at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:661)
	at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:426)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:592)
	at org.eclipse.ui.internal.EditorReference.getEditor(EditorReference.java:263)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2739)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2651)
	at org.eclipse.ui.internal.WorkbenchPage.access$13(WorkbenchPage.java:2643)
	at org.eclipse.ui.internal.WorkbenchPage$10.run(WorkbenchPage.java:2595)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:67)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2590)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2574)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2557)
	at com.adobe.flexbuilder.ui.actions.OpenStartPageAction.run(OpenStartPageAction.java:76)
	at org.eclipse.ui.internal.PluginAction.runWithEvent(PluginAction.java:256)
	at org.eclipse.ui.internal.WWinPluginAction.runWithEvent(WWinPluginAction.java:229)
	at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:546)
	at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:490)
	at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:402)
	at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:66)
	at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1101)
	at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3319)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:2971)
	at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2389)
	at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2353)
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
i'm newbie at eclipse, help please......

---

