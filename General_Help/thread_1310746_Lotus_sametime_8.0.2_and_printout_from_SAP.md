---
title: "Lotus sametime 8.0.2 and printout from SAP"
date: 2009-11-02
forum: General Help
---

### Post by sowjendra on 2009-11-02
Hi,

1. I have successfully installed Ubuntu 9.10. I have also installed Lotus notes with sametime 8.0.2. Initially i was not able to open Lotus notes. and after following instructions from [http://ubuntuforums.org/showthread.php?t=1306492&highlight=lotus+notes](http://ubuntuforums.org/showthread.php?t=1306492&highlight=lotus+notes)
[http://ubuntuforums.org/showthread.php?t=1287766&highlight=lotus+notes](http://ubuntuforums.org/showthread.php?t=1287766&highlight=lotus+notes)
these two links now i am able to login into lotus notes and sametime. I can send messages from Lotusnotes, where as i am not able to open the chat window from Same time.  I get the following error when the chat window is clicked.

2009/11/06 02:53:02.755 SEVERE Unhandled event loop exception ::class.method=unknown ::thread=main ::loggername=org.eclipse.ui
2009/11/06 02:53:02.756 SEVERE Failed to execute runnable (java.lang.NullPointerException) ::class.method=unknown ::thread=main ::loggername=org.eclipse.ui

    org.eclipse.swt.SWTException: Failed to execute runnable (java.lang.NullPointerException)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.SWT.error(Unknown Source)
    at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
    at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
    at org.eclipse.ui.internal.Workbench.runEventLoop(Unknown Source)
    at org.eclipse.ui.internal.Workbench.runUI(Unknown Source)
    at org.eclipse.ui.internal.Workbench.createAndRunWorkbench(Unknown Source)
    at org.eclipse.ui.PlatformUI.createAndRunWorkbench(Unknown Source)
    at com.ibm.rcp.personality.framework.internal.RCPApplication.run(Unknown Source)
    at org.eclipse.core.internal.runtime.PlatformActivator$1.run(Unknown Source)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.runApplication(Unknown Source)
    at org.eclipse.core.runtime.internal.adaptor.EclipseAppLauncher.start(Unknown Source)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(Unknown Source)
    at org.eclipse.core.runtime.adaptor.EclipseStarter.run(Unknown Source)
    at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
    at sun.reflect.NativeMethodAccessorImpl.invoke(Unknown Source)
    at sun.reflect.DelegatingMethodAccessorImpl.invoke(Unknown Source)
    at java.lang.reflect.Method.invoke(Unknown Source)
    at org.eclipse.core.launcher.Main.invokeFramework(Unknown Source)
    at org.eclipse.core.launcher.Main.basicRun(Unknown Source)
    at org.eclipse.core.launcher.Main.run(Unknown Source)
    at com.ibm.rcp.core.internal.launcher.Main.startLaunch(Unknown Source)
    at com.ibm.rcp.core.internal.launcher.Main.main(Unknown Source)
Caused by: java.lang.NullPointerException
    at com.ibm.collaboration.realtime.chatwindow.ImChatWindowHandler.updateToolBars(Unknown Source)
    at com.ibm.collaboration.realtime.chatwindow.ImChatWindowHandler.access$72(Unknown Source)
    at com.ibm.collaboration.realtime.chatwindow.ImChatWindowHandler$84.run(Unknown Source)
    at org.eclipse.swt.widgets.RunnableLock.run(Unknown Source)
    ... 22 more

2. We are using SAPGUI version 7.10 ver 9 in ubuntu 9.04 i was able to take SAP printouts from this , now in Ubuntu 9.10 I am not able to take printouts. Following error is coming 

Print request processing log
----------------------------------------------

Errors occurred processing this print request
--------------------------------------------------------------------

Error during print request output. l_rc = 99
There may be no printout


Most important attributes of spool request
-------------------------------------------
Request number 21369

Request name LIST1S LOCL RSMON000_REM
Client 555
Owner REMOTE
Request attributes
Time created   2009110606344700
Remaining life  +00008000000
Dispo 1 (Go/Hold) G
Dispo 2 (Keep/Delete)     K
Dispo 3 (Indirect/Direct) D
Default output device LOCL
Default no. copies  1
Format X_65_200
Main print request characteristics
------------------------------------------------
Spool request number 21369
Print request number 1
Print request attributes
Time created   2009110606344700
Output device LOCL
Format X_65_200

Character converter active when first problem occurred
-----------------------------------------------------------------
No information available

Please help me out

---

### Post by sowjendra on 2010-05-07
Hi..

I Installed ubuntu 10.04 LTS and in that  I installed Lotus notes 8.02 with sametime. Same problem is repeating in this Ubuntu version also .. Please help me out ..

Surendra

---

