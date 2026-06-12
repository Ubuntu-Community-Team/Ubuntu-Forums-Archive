---
title: "Android SDK: DDMS Crash"
date: 2011-12-07
forum: General Help
---

### Post by arky on 2011-12-07
The Android SDK tools/ddms tool crashes when I select the device. Can some help solve this problem. I am running sun-java6-jdk. 

Full pastebin here: [http://paste.ubuntu.com/762786/]("http://paste.ubuntu.com/762786/")

09:51:09 E/ddms: shutting down due to uncaught exception
09:51:09 E/ddms: Failed to execute runnable (java.lang.ArrayIndexOutOfBoundsException: -1)
org.eclipse.swt.SWTException: Failed to execute runnable (java.lang.ArrayIndexOutOfBoundsException: -1)
	at org.eclipse.swt.SWT.error(Unknown Source)
	at org.eclipse.swt.SWT.error(Unknown Source)
	at org.eclipse.swt.widgets.Synchronizer.runAsyncMessages(Unknown Source)
	at org.eclipse.swt.widgets.Display.runAsyncMessages(Unknown Source)
	at org.eclipse.swt.widgets.Display.readAndDispatch(Unknown Source)
	at com.android.ddms.UIThread.runUI(UIThread.java:517)
	at com.android.ddms.Main.main(Main.java:116)
Caused by: java.lang.ArrayIndexOutOfBoundsException: -1
	at org.eclipse.jface.viewers.AbstractTableViewer$VirtualManager.resolveElement(AbstractTableViewer.java:100)
	at org.eclipse.jface.viewers.AbstractTableViewer$1.handleEvent(AbstractTableViewer.java:70)
	at org.eclipse.swt.widgets.EventTable.sendEvent(Unknown Source)
	at org.eclipse.swt.widgets.Widget.sendEvent(Unknown Source)

---

