---
title: "Eclipse PHP error"
date: 2011-04-02
forum: General Help
---

### Post by Guenhwyvar on 2011-04-02
I have removed eclipse and tried reinstalling. I have just added eclipse php, but I cant get rid of this error whenever I open a php file. It php file opens clear.


```

eclipse.buildId=M20100211-1343
java.version=1.6.0_20
java.vendor=Sun Microsystems Inc.
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_GB
Command-line arguments:  -os linux -ws gtk -arch x86 -clean


Error
Sat Apr 02 18:10:00 BST 2011
Unhandled event loop exception

java.lang.NoClassDefFoundError: org/eclipse/wst/css/ui/internal/contentassist/CSSStructuredContentAssistProcessor
    at org.eclipse.php.internal.ui.editor.configuration.PHPStructuredTextViewerConfiguration.getContentAssistProcessors(PHPStructuredTextViewerConfiguration.java:183)
    at org.eclipse.php.internal.ui.editor.configuration.PHPStructuredTextViewerConfiguration.addContentAssistProcessors(PHPStructuredTextViewerConfiguration.java:259)
    at org.eclipse.php.internal.ui.editor.configuration.PHPStructuredTextViewerConfiguration.getContentAssistProcessors(PHPStructuredTextViewerConfiguration.java:161)
    at org.eclipse.php.internal.ui.editor.configuration.PHPStructuredTextViewerConfiguration.addContentAssistProcessors(PHPStructuredTextViewerConfiguration.java:259)
    at org.eclipse.php.internal.ui.editor.configuration.PHPStructuredTextViewerConfiguration.getPHPContentAssistant(PHPStructuredTextViewerConfiguration.java:243)
    at org.eclipse.php.internal.ui.editor.configuration.PHPStructuredTextViewerConfiguration.getPHPContentAssistant(PHPStructuredTextViewerConfiguration.java:209)
    at org.eclipse.php.internal.ui.editor.configuration.PHPStructuredTextViewerConfiguration.getContentAssistProcessors(PHPStructuredTextViewerConfiguration.java:154)
    at org.eclipse.wst.sse.ui.StructuredTextViewerConfiguration.getContentAssistant(StructuredTextViewerConfiguration.java:286)
    at org.eclipse.wst.sse.ui.internal.StructuredTextViewer.configure(StructuredTextViewer.java:208)
    at org.eclipse.php.internal.ui.editor.PHPStructuredTextViewer.configure(PHPStructuredTextViewer.java:445)
    at org.eclipse.ui.texteditor.AbstractTextEditor.createPartControl(AbstractTextEditor.java:3323)
    at org.eclipse.ui.texteditor.StatusTextEditor.createPartControl(StatusTextEditor.java:53)
    at org.eclipse.ui.texteditor.AbstractDecoratedTextEditor.createPartControl(AbstractDecoratedTextEditor.java:427)
    at org.eclipse.wst.sse.ui.StructuredTextEditor.createPartControl(StructuredTextEditor.java:1334)
    at org.eclipse.php.internal.ui.editor.PHPStructuredEditor.createPartControl(PHPStructuredEditor.java:2243)
    at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:662)
    at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:462)
    at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
    at org.eclipse.ui.internal.EditorReference.getEditor(EditorReference.java:286)
    at org.eclipse.ui.internal.EditorManager.findEditor(EditorManager.java:403)
    at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2799)
    at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2762)
    at org.eclipse.ui.internal.WorkbenchPage.access$11(WorkbenchPage.java:2754)
    at org.eclipse.ui.internal.WorkbenchPage$10.run(WorkbenchPage.java:2705)
    at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
    at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2701)
    at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2685)
    at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2668)
    at org.eclipse.ui.ide.IDE.openEditorOnFileStore(IDE.java:1151)
    at org.eclipse.ui.internal.ide.actions.OpenLocalFileAction.run(OpenLocalFileAction.java:107)
    at org.eclipse.ui.internal.ide.actions.OpenLocalFileAction.run(OpenLocalFileAction.java:76)
    at org.eclipse.ui.internal.PluginAction.runWithEvent(PluginAction.java:251)
    at org.eclipse.ui.internal.WWinPluginAction.runWithEvent(WWinPluginAction.java:229)
    at org.eclipse.jface.action.ActionContributionItem.handleWidgetSelection(ActionContributionItem.java:584)
    at org.eclipse.jface.action.ActionContributionItem.access$2(ActionContributionItem.java:501)
    at org.eclipse.jface.action.ActionContributionItem$5.handleEvent(ActionContributionItem.java:411)
    at org.eclipse.swt.widgets.EventTable.sendEvent(EventTable.java:84)
    at org.eclipse.swt.widgets.Widget.sendEvent(Widget.java:1176)
    at org.eclipse.swt.widgets.Display.runDeferredEvents(Display.java:3493)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3112)
    at org.eclipse.ui.internal.Workbench.runEventLoop(Workbench.java:2405)
    at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2369)
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


```

---

