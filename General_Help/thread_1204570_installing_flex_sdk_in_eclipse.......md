---
title: "installing flex sdk in eclipse......"
date: 2009-07-04
forum: General Help
---

### Post by abhilashm86 on 2009-07-04
i downloaded flex plugin for eclipse, after installing it in home directory, editor is not launching, error given was,```

org.eclipse.jface.util.Assert$AssertionFailedException: Assertion failed: 
	at org.eclipse.jface.util.Assert.isTrue(Assert.java:179)
	at org.eclipse.jface.util.Assert.isTrue(Assert.java:164)
	at com.adobe.flexbuilder.editors.derived.editor.FlexMultiPageEditorPart.setActivePage(FlexMultiPageEditorPart.java:569)
	at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.setActivePage(CodeAndDesignEditor.java:647)
	at com.adobe.flexbuilder.editors.mxml.MXMLEditor.setActivePage(MXMLEditor.java:487)
	at com.adobe.flexbuilder.editors.derived.editor.FlexMultiPageEditorPart.createPartControl(FlexMultiPageEditorPart.java:235)
	at com.adobe.flexbuilder.editors.common.editor.CodeAndDesignEditor.createPartControl(CodeAndDesignEditor.java:162)
	at org.eclipse.ui.internal.EditorReference.createPartHelper(EditorReference.java:662)
	at org.eclipse.ui.internal.EditorReference.createPart(EditorReference.java:462)
	at org.eclipse.ui.internal.WorkbenchPartReference.getPart(WorkbenchPartReference.java:595)
	at org.eclipse.ui.internal.EditorReference.getEditor(EditorReference.java:286)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditorBatched(WorkbenchPage.java:2857)
	at org.eclipse.ui.internal.WorkbenchPage.busyOpenEditor(WorkbenchPage.java:2762)
	at org.eclipse.ui.internal.WorkbenchPage.access$11(WorkbenchPage.java:2754)
	at org.eclipse.ui.internal.WorkbenchPage$10.run(WorkbenchPage.java:2705)
	at org.eclipse.swt.custom.BusyIndicator.showWhile(BusyIndicator.java:70)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2701)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2685)
	at org.eclipse.ui.internal.WorkbenchPage.openEditor(WorkbenchPage.java:2668)
	at org.eclipse.ui.ide.IDE.openEditor(IDE.java:683)
	at com.adobe.flexbuilder.editors.common.ui.project.FlexProjectUI.openEditor(FlexProjectUI.java:264)
	at com.adobe.flexbuilder.editors.common.ui.project.FlexProjectUI.access$2(FlexProjectUI.java:259)
	at com.adobe.flexbuilder.editors.common.ui.project.FlexProjectUI$1.runInUIThread(FlexProjectUI.java:185)
	at org.eclipse.ui.progress.UIJob$1.run(UIJob.java:95)
	at org.eclipse.swt.widgets.RunnableLock.run(RunnableLock.java:35)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Synchronizer.java:134)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Display.java:3468)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Display.java:3115)
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
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:39)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:25)
	at java.lang.reflect.Method.invoke(Method.java:597)
	at org.eclipse.equinox.launcher.Main.invokeFramework(Main.java:559)
	at org.eclipse.equinox.launcher.Main.basicRun(Main.java:514)
	at org.eclipse.equinox.launcher.Main.run(Main.java:1311)


```
i don't know how to correct it, please help ..............

---

### Post by dmartin on 2009-07-05
Flex for Linux is not compatible with Eclipse Ganymede (3.4).  You have to use the Europa (3.3) version.

---

### Post by abhilashm86 on 2009-07-05
oh i simply downloaded whole eclipse, fine then should i download eclipse from their website and tar and run it in home directory, this procedure is correct??
if i install eclipse from synaptic, then it'll be installed in /etc, after which i can't install flex plugin, it says error, cannot write??
which is better way of installing eclipse?? extract or syanptic??

---

### Post by abhilashm86 on 2009-07-05
can anyone give me website link where to download Europa (3.3) version of eclipse?? i tried thrice and flex din't work with eclipse, so kinda fed up, please suggest a link, as in eclipse.org i find only some eclipse and plugins, i want Europa (3.3) compatible with ubuntu.......

---

### Post by dmartin on 2009-07-05
[http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/europa/winter/eclipse-java-europa-winter-linux-gtk.tar.gz](http://www.eclipse.org/downloads/download.php?file=/technology/epp/downloads/release/europa/winter/eclipse-java-europa-winter-linux-gtk.tar.gz)

---

### Post by dmartin on 2009-07-05
As far as installing, I have a folder in my Home folder called "Applications" and I put custom apps there (Google Earth, Eclipse, JBoss, etc).

The file I linked above can be extracted anywhere, and the eclipse file can just be run.  Though, once you install Flex Builder, another executable binary is provided.

---

### Post by jap1968 on 2009-09-17
I have been working with Flash on Linux since some time ago.

Initialy I worked With Eclipse 3.3 and 3.4 using ASDT plugin (just AS2 support) and recently with AXDT (AS3 support).

I have faced multiple problems to obtain a working framework. Luckily, the **Eclipse 3.5** version is much less problem prone and **much easier to install**.

I have written a couple of blog entries about how to [setup a Flash development on Linux]("http://netpatia.blogspot.com/2009/09/flash-development-on-linux.html") (**Ubuntu 9.04**, 32bit) so, you may be interested in having a Look at these.

---

### Post by Huss on 2010-02-10
Hi Jap1986,

I followed your blog entry and installed the AXDT plug-in, but after opening an MXML file received the same error message mentioned by abh...

Do you have any other advice?

Cheers

Huss

---

### Post by tuthmosis on 2010-07-06
Have been trying to do Flex dev. on Ubuntu 10.04 AMD64 64bit.

The installation process messing with JRE 32bit isn't working for me. (For many reasons)

Would it be easier and cleaner to simply download the [Flex SDK]("http://www.adobe.com/cfusion/entitlement/index.cfm?e=flex4sdk") and use it through Eclipse ?
If not, anyone knows a good WINE equivalent that actually works for something ?  (Other than some shooting video games.)

Thanks.. i am desperate !

---

### Post by jap1968 on 2010-07-07
Flash development in Linux should not be a problem right now with the currently available tools.

Since I updated to Eclipse 3.5, I am having no problems at all. :D

I have recently installed Eclipse 3.5 + AXDT in a couple of machines, both in Ubuntu 10.04. The first one being 32 bit, but the second one with the 64 bit version. Both versions are working properly.

AXDT already includes a version of the open source flex sdk, so you do not need to worry about installing additional versions

If you are setting up a 64 bit environment, use Sun JDK 64 bits! I do not recommend using OpenJDK ( I tried but I was not able to achieve a working environment)

---

### Post by tuthmosis on 2010-07-07
Is there a plugin for Air ?

---

### Post by olgis on 2010-10-18
Great AIR application called **desginview** - fee of charge
You can download from the **adobe marketplace** (a place to share / sell AIR applications).

---

