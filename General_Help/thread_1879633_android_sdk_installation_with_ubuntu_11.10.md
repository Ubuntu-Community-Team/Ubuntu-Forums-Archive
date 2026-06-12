---
title: "android sdk installation with ubuntu 11.10??"
date: 2011-11-11
forum: General Help
---

### Post by sathyashrayan on 2011-11-11
laptop: Dell Inspiron N5030.. 
 I am breaking my head hard to make this android sdk work with the new 
 ubuntu 11.10 version. But the outcome is a total failure. When i give 
 "android" in terminal and go to AVD manager, create new AVD and click start crashes 
 with the following error: 

 
```
ava.awt.HeadlessException 
         at sun.awt.HeadlessToolkit.getScreenResolution(HeadlessToolkit.java: 
 221) 
         at 
 com.android.sdkuilib.internal.widgets.AvdStartDialog.getMonitorDpi(AvdStartDialog.java: 
 420) 
         at 
 com.android.sdkuilib.internal.widgets.AvdStartDialog.createDialogContent(AvdStartDialog.java: 
 179) 
         at 
 com.android.sdkuilib.ui.GridDialog.createDialogArea(GridDialog.java: 
 76) 
         at org.eclipse.jface.dialogs.Dialog.createContents(Dialog.java:760) 
         at org.eclipse.jface.window.Window.create(Window.java:431) 
         at org.eclipse.jface.dialogs.Dialog.create(Dialog.java:1089) 
         at org.eclipse.jface.window.Window.open(Window.java:790) 
         at 
 com.android.sdkuilib.internal.widgets.AvdSelector.onStart(AvdSelector.java: 
 1035) 
         at com.android.sdkuilib.internal.widgets.AvdSelector.access 
 $600(AvdSelector.java:76) 
         at com.android.sdkuilib.internal.widgets.AvdSelector 
 $7.widgetSelected(AvdSelector.java:317) 
         at org.eclipse.swt.widgets.TypedListener.handleEvent(Unknown Source) 
         at org.eclipse.swt.widgets.EventTable.sendEvent(Unknown Source) 
         at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source) 
         at org.eclipse.swt.widgets.Display.runDeferredEvents(Unknown Source) 
         at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source) 
         at 
 com.android.sdkuilib.internal.repository.sdkman2.SdkUpdaterWindowImpl2.open(SdkUpdaterWindowImpl2.java: 
 158) 
         at 
 com.android.sdkuilib.repository.SdkUpdaterWindow.open(SdkUpdaterWindow.java: 
 154) 
         at com.android.sdkmanager.Main.showSdkManagerWindow(Main.java:335) 
         at com.android.sdkmanager.Main.doAction(Main.java:307) 
         at com.android.sdkmanager.Main.run(Main.java:119) 
         at com.android.sdkmanager.Main.main(Main.java:102) 
```I have even uninstalled eclips. 
 
Any helps?

---

### Post by sathyashrayan on 2011-11-19
Hi all..It is working now. I really don't know how it got cleared. May be new update from the ubuntu. Now i am planning to use VIM as an editor and netbean IDE for just to build / compile and run.

---

### Post by drillerccg on 2011-11-24
[http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62](http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62)

---

### Post by sathyashrayan on 2011-11-24
> **drillerccg said:**
> [http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62](http://forum.xda-developers.com/showpost.php?p=19446284&postcount=62)

Thanks for the link..

---

