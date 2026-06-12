---
title: "Vuze  in 11.04 crashes. (Java swt problem?)"
date: 2011-09-05
forum: General Help
---

### Post by pwicken on 2011-09-05
Tried to install Vuze from Software Center. The interface shows up, and closes after a few seconds.

According to this I would need Sun/Oracle Java to run Vuze
[https://help.ubuntu.com/community/AzureusHowTo]("https://help.ubuntu.com/community/AzureusHowTo")

Which I have:
```
java version "1.6.0_26"
Java(TM) SE Runtime Environment (build 1.6.0_26-b03)
Java HotSpot(TM) 64-Bit Server VM (build 20.1-b02, mixed mode)
```

Vuze error log:


```
[9/5/11 6:58 PM] Log File Opened for Vuze 4.3.0.6

[18:58:59] DEBUG::Mon Sep 05 18:58:59 CEST 2011  Successfully migrated key management
[18:59:03] [stderr] DEBUG::Mon Sep 05 18:59:03 CEST 2011::org.gudy.azureus2.core3.util.DebugLight::printStackTrace::38:
[18:59:03] DEBUG::Mon Sep 05 18:59:03 CEST 2011::org.gudy.azureus2.core3.util.DebugLight::printStackTrace::38:
[18:59:03] [stderr]   java.lang.IllegalArgumentException: Unknown operation: get-mode
[18:59:03] [stderr] 	at com.aelitis.azureus.ui.swt.browser.listener.VuzeListener.handleMessage(VuzeListener.java:64)
[18:59:03] [stderr] 	at com.aelitis.azureus.ui.swt.browser.msg.MessageDispatcherSWT$2.run(MessageDispatcherSWT.java:193)
[18:59:03] [stderr] 	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)
[18:59:03] [stderr] 
[18:59:03]   java.lang.IllegalArgumentException: Unknown operation: get-mode
	at com.aelitis.azureus.ui.swt.browser.listener.VuzeListener.handleMessage(VuzeListener.java:64)
	at com.aelitis.azureus.ui.swt.browser.msg.MessageDispatcherSWT$2.run(MessageDispatcherSWT.java:193)
	at org.gudy.azureus2.core3.util.AEThread2$threadWrapper.run(AEThread2.java:287)

```

Anybody got any ideas?

---

