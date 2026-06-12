---
title: "Eclipse startup problem"
date: 2009-07-08
forum: General Help
---

### Post by hechim on 2009-07-08
Hi,
I am running Eclipse 3.2.2 on Ubuntu 8.04
It usually works perfectly well. However, when I tried to open it today, it gave me the following error message:

An error has occurred. See the log file
/home/[*my_username*]/workspace/.metadata/.log.

I did not change anything on Ubuntu since my last login, I really don't know what happened.

Please I need help on this fast.

Thanks,
hechim

---

### Post by t4thfavor on 2009-07-08
I suggest you see the log referenced, and se if you can decipher it. Without that we cannot help you.

---

### Post by hechim on 2009-07-08
I can't understand what the file says.
Would you like me to post it here or send it to you or something? (it's rather long)

---

### Post by hechim on 2009-07-09
Here is the log file:

!SESSION 2009-07-09 13:09:16.701 -----------------------------------------------
eclipse.buildId=M20070212-1330
java.fullversion=GNU libgcj 4.2.3 (Ubuntu 4.2.3-2ubuntu6)
BootLoader constants: OS=linux, ARCH=x86, WS=gtk, NL=en_US
Command-line arguments:  -os linux -ws gtk -arch x86

!ENTRY org.eclipse.osgi 4 0 2009-07-09 13:09:34.472
!MESSAGE Application error
!STACK 1
org.eclipse.swt.SWTError: XPCOM error -2147467262
   at org.eclipse.swt.browser.Mozilla.error(Mozilla.java:1638)
   at org.eclipse.swt.browser.Mozilla.setText(Mozilla.java:1861)
   at org.eclipse.swt.browser.Browser.setText(Browser.java:737)
   at org.eclipse.jdt.internal.ui.infoviews.JavadocView.setInput(JavadocView.java:465)
   at org.eclipse.jdt.internal.ui.infoviews.JavadocView.setBackground(JavadocView.java:386)
   at org.eclipse.jdt.internal.ui.infoviews.AbstractInfoView.inititalizeColors(AbstractInfoView.java:327)
   at org.eclipse.jdt.internal.ui.infoviews.AbstractInfoView.createPartControl(AbstractInfoView.java:191)
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
   at org.eclipse.swt.widgets.Synchronizer.syncExec(Synchronizer.java:178)
   at org.eclipse.ui.internal.UISynchronizer.syncExec(UISynchronizer.java:150)
   at org.eclipse.swt.widgets.Display.syncExec(Display.java:4021)
   at org.eclipse.ui.internal.StartupThreading.runWithoutExceptions(StartupThreading.java:94)
   at org.eclipse.ui.internal.Workbench.init(Workbench.java:1356)
   at org.eclipse.ui.internal.Workbench.runUI(Workbench.java:2312)
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
   at java.lang.reflect.Method.invoke(libgcj.so.81)
   at org.eclipse.core.launcher.Main.invokeFramework(Main.java:336)
   at org.eclipse.core.launcher.Main.basicRun(Main.java:280)
   at org.eclipse.core.launcher.Main.run(Main.java:977)
   at org.eclipse.core.launcher.Main.main(Main.java:952)

!ENTRY org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE The following is a complete list of bundles which are not resolved, see the prior log entry for the root cause if it exists:
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.compat[/email]ibility_3.2.0.I20060605-1400/ [18] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.cheatsheets_3.2.1.R321_v20060720.jar[/email] [27] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench.texteditor_3.2.0.v20060605-1400.jar[/email] [30] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.views.properties.tabbed_3.2.1.M20060830-0800.jar[/email] [32] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.console_3.1.100.v20060605.jar[/email] [39] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.equinox.preferences_3.2.1.R32x_v20060717.jar[/email] [40] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.presentations.r21_3.2.0.I20060605-1400.jar[/email] [41] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.expressions_3.2.2.r322_v20070109a.jar[/email] [43] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.jobs_3.2.0.v20060603.jar[/email] [44] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.platfo[/email]rm_3.2.2.r322_v20070117b/ [53] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filebuffers_3.2.1.r321_v20060721.jar[/email] [57] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt.gtk.linux.x86_3.2.2.v3236.jar[/email] [61] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ssh2_3.2.1.M20061205.jar[/email] [68] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime.compatibility_3.1.100.v20060603.jar[/email] [76] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.appserver_3.1.100.v20060602.jar[/email] [79] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.base_3.2.2.R322_v20061207.jar[/email] [80] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.ui_3.2.2.R32x_v20070111.jar[/email] [84] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.376
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filesystem.linux.x86_1.0.0.v20060603.jar[/email] [85] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.core_3.2.1.v20060823.jar[/email] [86] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.core_3.2.2.M20061114.jar[/email] [89] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.resources.compatibility_3.2.0.v20060603.jar[/email] [93] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.intro_3.2.2.R322_v20061214.jar[/email] [97] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime.compatibility.regist[/email]ry_3.2.1.R32x_v20060907/ [98] was not resolved.
!SUBENTRY 2 org.eclipse.core.runtime.compatibility.registry 2 0 2009-07-09 13:09:36.377
!MESSAGE Missing host org.eclipse.equinox.registry_[3.2.0,3.3.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.help_3.2.2.R322_v20061213.jar[/email] [99] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.compare_3.2.1.M20060711.jar[/email] [102] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.navigator.resources_3.2.1.M20060906-0800b.jar[/email] [103] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.osgi_3.2.2.R32x_v20070118.jar[/email] [113] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.ide_3.2.1.M20060915-1030.jar[/email] [116] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.variables_3.1.100.v20060605.jar[/email] [120] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.resources_3.2.2.R32x_v20061218.jar[/email] [128] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.externaltools_3.1.101.r321_v20060802.jar[/email] [132] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.core_3.2.2.M20061205.jar[/email] [133] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.ui_3.2.1.M200608151725.jar[/email] [134] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.equinox.common_3.2.0.v20060603.jar[/email] [139] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.swt_3.2.2.v3236b.jar[/email] [147] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.team.cvs.ui_3.2.2.M20061121.jar[/email] [154] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/com.ibm.icu_3.4.5.20061213.jar[/email] [156] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.webapp[/email]_3.2.2.R322_v20061114/ [157] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.core.refactoring_3.2.1.r321_v20060823.jar[/email] [159] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.debug.ui_3.2.2.r322_v20070202.jar[/email] [171] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.ant.core_3.1.100.v20060531.jar[/email] [173] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.equinox.registry_3.2.1.R32x_v20060814.jar[/email] [177] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.377
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.navigator_3.2.1.M20060913-0800.jar[/email] [186] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.configurator_3.2.2.R32x_v20070111.jar[/email] [187] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.browser_3.2.0.v20060602.jar[/email] [193] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.ltk.ui.refactoring_3.2.2.r322_v20070124.jar[/email] [195] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.contenttype_3.2.0.v20060603.jar[/email] [201] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.runtime_3.2.0.v20060603.jar[/email] [203] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.workbench_3.2.2.M20070119-0800.jar[/email] [207] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.editors_3.2.1.r321_v20060721.jar[/email] [216] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.rcp_3.2.0.v20060605.jar[/email] [222] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.core.filesystem_1.0.0.v20060603.jar[/email] [230] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.core.linux_3.2.0.v20060605.jar[/email] [234] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.help.ui_3.2.0.v20060602.jar[/email] [236] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui_3.2.1.M20061108.jar[/email] [244] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.search_3.2.1.r321_v20060726.jar[/email] [245] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.core_3.2.3.R32x_v20070118.jar[/email] [252] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.update.scheduler_3.2.2.R32x_v20061214.jar[/email] [257] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.views_3.2.1.M20060906-0800.jar[/email] [263] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.ui.intro.univer[/email]sal_3.2.1.R321_v20060905/ [274] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.make.ui_3.1.2.200706181825.jar[/email] [281] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.378
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt_3.1.2.200706181825.jar[/email] [282] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.core_3.1.2.200706181825.jar[/email] [283] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.managedbuilder.core_3.1.2.200706181825.jar[/email] [285] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.ui_3.1.2.200706181825.jar[/email] [286] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.managedbuilder.gnu.ui_3.1.2.200706181825.jar[/email] [287] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.core.linux[/email].x86_3.1.2.200706181825/ [288] was not resolved.
!SUBENTRY 2 org.eclipse.cdt.core.linux.x86 2 0 2009-07-09 13:09:36.379
!MESSAGE Missing host org.eclipse.cdt.core_[3.1.2,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.managedbuilder.ui_3.1.2.200706181825.jar[/email] [289] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.debug.ui_3.1.2.200706181825.jar[/email] [290] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.debug.mi.ui_3.1.2.200706181825.jar[/email] [293] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.debug.core_3.1.2.200706181825.jar[/email] [294] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.launch_3.1.2.200706181825.jar[/email] [297] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.debug.mi.core_3.1.2.200706181825.jar[/email] [299] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.core.linux[/email]_3.1.2.200706181825/ [300] was not resolved.
!SUBENTRY 2 org.eclipse.cdt.core.linux 2 0 2009-07-09 13:09:36.379
!MESSAGE Missing host org.eclipse.cdt.core_[3.1.2,4.0.0).
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.doc.user_3.1.2.200706181825.jar[/email] [301] was not resolved.
!SUBENTRY 1 org.eclipse.osgi 2 0 2009-07-09 13:09:36.379
!MESSAGE Bundle [email]update@plugins/org.eclipse.cdt.make.core_3.1.2.200706181825.jar[/email] [302] was not resolved.

---

### Post by nikhilk on 2009-07-09
You have probably changed something related to Firefox (updated to 3.5 maybe?).

See if [this]("http://sandakith.wordpress.com/2008/07/11/eclipse-ganymede-startup-problem-in-ubuntu-orgeclipseswtswterror-xpcom-erro/") helps.

---

### Post by hechim on 2009-07-09
I have not changed anything in Firefox.
I followed the link and followed the instructions step by step, but I am still getting the same error with the same log file.
I was thinking of reinstalling Eclipse, but I want to make sure that there is no other solution first.

Thanks

---

### Post by hechim on 2009-07-09
I re-installed the whole thing but it's still not working :'( help

---

