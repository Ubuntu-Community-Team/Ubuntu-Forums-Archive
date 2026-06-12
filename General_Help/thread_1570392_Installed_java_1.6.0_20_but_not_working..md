---
title: "Installed java 1.6.0_20 but not working."
date: 2010-09-08
forum: General Help
---

### Post by nik16v on 2010-09-08
Hi to all. 
I am a new user of ubuntu 10.04.
I installed the above version to a pc at my work and i 'm trying to make it work with a program we use through explorer (Firefox/Internet Explorer) and uses java.
I managed through search to install and use as default java 1.6.0_20 but when i 'm trying to use the tab of the program. It appears a message that says
 "Error. Click here for details."
Details -> The application failed to run. Details->

[Log File]
Java Plug-in 1.6.0_20
Using JRE version 1.6.0_20-b02 Java HotSpot(TM) Client VM
User home directory = /home/......
------------------------------------------------------
java.lang.reflect.InvocationTargetException
    at com.sun.deploy.util.DeployAWTUtil.invokeAndWait(DeployAWTUtil.java:116)
    at sun.plugin2.applet.Plugin2Manager.runOnEDT(Plugin2Manager.java:3415)
    at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2967)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1444)
    at java.lang.Thread.run(Thread.java:619)
Caused by: java.lang.SecurityException: trusted loader attempted to load sandboxed resource from [https://.........../........-xml/static/applet/lib/swing-layout.jar](https://.........../........-xml/static/applet/lib/swing-layout.jar)
    at com.sun.deploy.security.CPCallbackHandler$ParentCallback.check(CPCallbackHandler.java:308
    at com.sun.deploy.security.CPCallbackHandler$ParentCallback.access$1400(CPCallbackHandler.java:121)
    at com.sun.deploy.security.CPCallbackHandler$ChildElement.checkResource(CPCallbackHandler.java:473)
    at com.sun.deploy.security.DeployURLClassPath$JarLoader.checkResource(DeployURLClassPath.java:790)
    at com.sun.deploy.security.DeployURLClassPath$JarLoader.getResource(DeployURLClassPath.java:890)
    at com.sun.deploy.security.DeployURLClassPath.getResource(DeployURLClassPath.java:231)
    at sun.plugin2.applet.Plugin2ClassLoader$2.run(Plugin2ClassLoader.java:796)
    at java.security.AccessController.doPrivileged(Native Method)
    at sun.plugin2.applet.Plugin2ClassLoader.findClassHelper(Plugin2ClassLoader.java:785)
    at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:147)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
    at java.lang.ClassLoader.loadClass(ClassLoader.java:248
    at java.lang.Class.getDeclaredConstructors0(Native Method)
    at java.lang.Class.privateGetDeclaredConstructors(Class.java:2389)
    at java.lang.Class.getConstructor0(Class.java:2699)
    at java.lang.Class.newInstance0(Class.java:326)
    at java.lang.Class.newInstance(Class.java:308
    at sun.plugin2.applet.Plugin2Manager$12.run(Plugin2Manager.java:2955)
    at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:199)
    at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
    at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
    at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
    at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
    at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
    at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Exception: java.lang.reflect.InvocationTargetException
------------------------------------------------------------------------------------------------------

If anyone could help me i would appreciate.
Thank you all.

---

### Post by gandaran on 2010-09-08
> I installed the above version to a pc at my work and i 'm trying to make it work with a program we use through explorer (Firefox/Internet Explorer) and uses java.
internet explorer? are you running it in wine? how did you install the java? from the system repositories?

---

### Post by nik16v on 2010-09-08
My mistake. We all use XP and run it through I.E. or F.F.
I installed java through ubuntu application center and updated it through terminal.

---

### Post by gauravj on 2010-09-08
Hi

It appears that the problem is with
Caused by: java.lang.SecurityException: trusted loader attempted to load sandboxed resource from [https://.........../........-xml/sta...ing-layout.jar](https://.........../........-xml/sta...ing-layout.jar)

make the jar available locally by downloading it to system and 
placing it in ext directory of the jre.

---

### Post by nik16v on 2010-09-09
Thank you gauravj.
We made 1 step forward. 
Now i have another prob.
2 tabs come out every time i want to work with the program. (s1.xcf and s2.xcf) --> attached files.
Java works in the point that didn't but now a new error comes out.

[Log file]

Java Plug-in 1.6.0_20
Using JRE version 1.6.0_20-b02 Java HotSpot(TM) Client VM

----------------------------------------------------


load: class com.realobjects.preloadJvm not found.
java.lang.ClassNotFoundException: com.realobjects.preloadJvm
at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:219)
at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
at java.lang.ClassLoader.loadClass(ClassLoader.java:248
at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:532)
at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2940)
at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1444)
at java.lang.Thread.run(Thread.java:619)
Caused by: javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at java.net.HttpURLConnection.getResponseCode(HttpURLConnection.java:373)
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getResponseCode(HttpsURLConnectionImpl.java:318]("http://www.protocol.https.HttpsURLConnectionImpl.getResponseCode%28HttpsURLConnectionImpl.java:318"))
at sun.plugin2.applet.Applet2ClassLoader.getBytes(Applet2ClassLoader.java:535)
at sun.plugin2.applet.Applet2ClassLoader.access$000(Applet2ClassLoader.java:51)
at sun.plugin2.applet.Applet2ClassLoader$1.run(Applet2ClassLoader.java:192)
at java.security.AccessController.doPrivileged(Native Method)
at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:189)
... 6 more
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 23 more
Exception: java.lang.ClassNotFoundException: com.realobjects.preloadJvm
filetypes: [Ljava.lang.String;@4d76b4
java.lang.NullPointerException
at .............................applet.ArxeionXML$1.run(Unknown Source)
at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
java.lang.NullPointerException
at .............................applet.ArxeionXML$1.run(Unknown Source)
at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
java.lang.NullPointerException
at .........................applet.ArxeionXML$1.run(Unknown Source)
at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
java.lang.NullPointerException
at ................................applet.ArxeionXML$1.run(Unknown Source)
at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:597)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at .....................................applet.network.ARXdownload.getTableModelFromXml(Unknown Source)
at .................................applet.ArxeionXML.getDocList(Unknown Source)
at .................................applet.ArxeionXML$2.construct(Unknown Source)
at .................................applet.common.SwingWorker$2.run(Unknown Source)
at java.lang.Thread.run(Thread.java:619)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 16 more
getting info from: [https://............-1/arxeion-xml/pages/...................../prot_beta/file-mime-type?arx-file-name=B-1093.pdf](https://............-1/arxeion-xml/pages/...................../prot_beta/file-mime-type?arx-file-name=B-1093.pdf)
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 45 more
getting info from: [https://......................../arxeion-xml/pages/............/prot_beta/file-mime-type?arx-file-name=B-1093.pdf](https://......................../arxeion-xml/pages/............/prot_beta/file-mime-type?arx-file-name=B-1093.pdf)
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.isDoubleHtml(Unknown Source)
at ........................................applet.ArxeionXML.isValidFile(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 48 more
getting extension info from servlet...
getting info from: [https://....................../arxeion-xml/pages/................../prot_beta/file-mime-type?arx-file-name=B-1093.pdf](https://....................../arxeion-xml/pages/................../prot_beta/file-mime-type?arx-file-name=B-1093.pdf)
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.isValidExtension(Unknown Source)
at ........................................applet.ArxeionXML.isValidFile(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 48 more
isValidExtension result: false
Invalid ext
getting info from: [https://........................../arxeion-xml/pages/................../prot_beta/file-mime-type?arx-file-name=UTP5.pdf](https://........................../arxeion-xml/pages/................../prot_beta/file-mime-type?arx-file-name=UTP5.pdf)
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 45 more
getting info from: [https://..................../arxeion-xml/pages/............/prot_beta/file-mime-type?arx-file-name=UTP5.pdf](https://..................../arxeion-xml/pages/............/prot_beta/file-mime-type?arx-file-name=UTP5.pdf)
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.isDoubleHtml(Unknown Source)
at ........................................applet.ArxeionXML.isValidFile(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 48 more
getting extension info from servlet...
getting info from: [https://....................../arxeion-xml/pages/.............../prot_beta/file-mime-type?arx-file-name=UTP5.pdf](https://....................../arxeion-xml/pages/.............../prot_beta/file-mime-type?arx-file-name=UTP5.pdf)
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.isValidExtension(Unknown Source)
at ........................................applet.ArxeionXML.isValidFile(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 48 more
isValidExtension result: false
Invalid ext
getting info from: https:// ......................................../arxeion-xml/pages/............../prot_beta/file-mime-type?arx-file-name=%CE%9E%CE%B5%CE%BA%CE%B9%CE%BD%CF%8E%CE%BD%CF%84%CE%B1%CF%82+%CE%BC%CE%B5+%CF%84%CE%BF+Ubuntu+10.04.pdf
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 45 more
getting info from: https:// ......................................../arxeion-xml/pages/............./prot_beta/file-mime-type?arx-file-name=%CE%9E%CE%B5%CE%BA%CE%B9%CE%BD%CF%8E%CE%BD%CF%84%CE%B1%CF%82+%CE%BC%CE%B5+%CF%84%CE%BF+Ubuntu+10.04.pdf
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.isDoubleHtml(Unknown Source)
at ........................................applet.ArxeionXML.isValidFile(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 48 more
getting extension info from servlet...
getting info from: https:// ......................................../arxeion-xml/pages/............../prot_beta/file-mime-type?arx-file-name=%CE%9E%CE%B5%CE%BA%CE%B9%CE%BD%CF%8E%CE%BD%CF%84%CE%B1%CF%82+%CE%BC%CE%B5+%CF%84%CE%BF+Ubuntu+10.04.pdf
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.isValidExtension(Unknown Source)
at ........................................applet.ArxeionXML.isValidFile(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 48 more
isValidExtension result: false
Invalid ext
getting info from: https:// ......................................../arxeion-xml/pages/..................../prot_beta/file-mime-type?arx-file-name=tes1.txt
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 45 more
getting info from: https:// ......................................../arxeion-xml/pages/............../prot_beta/file-mime-type?arx-file-name=tes1.txt
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.isDoubleHtml(Unknown Source)
at ........................................applet.ArxeionXML.isValidFile(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 48 more
getting extension info from servlet...
getting info from: https:// ........................................arxeion-xml/pages/................/prot_beta/file-mime-type?arx-file-name=tes1.txt
javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getInputStream(HttpsURLConnectionImpl.java:234]("http://www.protocol.https.HttpsURLConnectionImpl.getInputStream%28HttpsURLConnectionImpl.java:234"))
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.common.ARXfileinfo.getExtension(Unknown Source)
at ........................................applet.ArxeionXML.isValidExtension(Unknown Source)
at ........................................applet.ArxeionXML.isValidFile(Unknown Source)
at ........................................applet.ArxeionXML.insertFileToDocs(Unknown Source)
at ........................................applet.ArxeionXML.access$6200(Unknown Source)
at ........................................applet.ArxeionXML$48.run(Unknown Source)
at java.security.AccessController.doPrivileged(Native Method)
at ........................................applet.ArxeionXML.menuFileOpenActionPerformed(Unknown Source)
at ........................................applet.ArxeionXML.access$4300(Unknown Source)
at ........................................applet.ArxeionXML$26.actionPerformed(Unknown Source)
at javax.swing.AbstractButton.fireActionPerformed(AbstractButton.java:1995)
at javax.swing.AbstractButton$Handler.actionPerformed(AbstractButton.java:2318
at javax.swing.DefaultButtonModel.fireActionPerformed(DefaultButtonModel.java:387)
at javax.swing.DefaultButtonModel.setPressed(DefaultButtonModel.java:242)
at javax.swing.AbstractButton.doClick(AbstractButton.java:357)
at javax.swing.plaf.basic.BasicMenuItemUI.doClick(BasicMenuItemUI.java:1223)
at javax.swing.plaf.basic.BasicMenuItemUI$Handler.mouseReleased(BasicMenuItemUI.java:1264)
at java.awt.Component.processMouseEvent(Component.java:6263)
at javax.swing.JComponent.processMouseEvent(JComponent.java:3267)
at java.awt.Component.processEvent(Component.java:6028
at java.awt.Container.processEvent(Container.java:2041)
at java.awt.Component.dispatchEventImpl(Component.java:4630)
at java.awt.Container.dispatchEventImpl(Container.java:2099)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.LightweightDispatcher.retargetMouseEvent(Container.java:4574)
at java.awt.LightweightDispatcher.processMouseEvent(Container.java:4238
at java.awt.LightweightDispatcher.dispatchEvent(Container.java:4168
at java.awt.Container.dispatchEventImpl(Container.java:2085)
at java.awt.Component.dispatchEvent(Component.java:4460)
at java.awt.EventQueue.dispatchEvent(EventQueue.java:599)
at java.awt.EventDispatchThread.pumpOneEventForFilters(EventDispatchThread.java:269)
at java.awt.EventDispatchThread.pumpEventsForFilter(EventDispatchThread.java:184)
at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:174)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:169)
at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:161)
at java.awt.EventDispatchThread.run(EventDispatchThread.java:122)
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 48 more
isValidExtension result: false
Invalid ext
load: class com.realobjects.eop.japplet.SwingEditorApplet not found.
java.lang.ClassNotFoundException: com.realobjects.eop.japplet.SwingEditorApplet
at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:219)
at java.lang.ClassLoader.loadClass(ClassLoader.java:307)
at java.lang.ClassLoader.loadClass(ClassLoader.java:248
at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Plugin2ClassLoader.java:532)
at sun.plugin2.applet.Plugin2Manager.createApplet(Plugin2Manager.java:2940)
at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Plugin2Manager.java:1444)
at java.lang.Thread.run(Thread.java:619)
Caused by: javax.net.ssl.SSLHandshakeException: java.security.cert.CertificateException: Certificate has been denied
at com.sun.net.ssl.internal.ssl.Alerts.getSSLException(Alerts.java:174)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.fatal(SSLSocketImpl.java:1623)
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:198
at com.sun.net.ssl.internal.ssl.Handshaker.fatalSE(Handshaker.java:192)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1074)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.processMessage(ClientHandshaker.java:128
at com.sun.net.ssl.internal.ssl.Handshaker.processLoop(Handshaker.java:529)
at com.sun.net.ssl.internal.ssl.Handshaker.process_record(Handshaker.java:465)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.readRecord(SSLSocketImpl.java:884)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.performInitialHandshake(SSLSocketImpl.java:1120)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1147)
at com.sun.net.ssl.internal.ssl.SSLSocketImpl.startHandshake(SSLSocketImpl.java:1131)
at sun.net.[www.protocol.https.HttpsClient.afterConnect(HttpsClient.java:434]("http://www.protocol.https.HttpsClient.afterConnect%28HttpsClient.java:434"))
at sun.net.[www.protocol.https.AbstractDelegateHttpsURLConnection.connect(AbstractDelegateHttpsURLConnection.java:166]("http://www.protocol.https.AbstractDelegateHttpsURLConnection.connect%28AbstractDelegateHttpsURLConnection.java:166"))
at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(HttpURLConnection.java:1049]("http://www.protocol.http.HttpURLConnection.getInputStream%28HttpURLConnection.java:1049"))
at java.net.HttpURLConnection.getResponseCode(HttpURLConnection.java:373)
at sun.net.[www.protocol.https.HttpsURLConnectionImpl.getResponseCode(HttpsURLConnectionImpl.java:318]("http://www.protocol.https.HttpsURLConnectionImpl.getResponseCode%28HttpsURLConnectionImpl.java:318"))
at sun.plugin2.applet.Applet2ClassLoader.getBytes(Applet2ClassLoader.java:535)
at sun.plugin2.applet.Applet2ClassLoader.access$000(Applet2ClassLoader.java:51)
at sun.plugin2.applet.Applet2ClassLoader$1.run(Applet2ClassLoader.java:192)
at java.security.AccessController.doPrivileged(Native Method)
at sun.plugin2.applet.Applet2ClassLoader.findClass(Applet2ClassLoader.java:189)
... 6 more
Caused by: java.security.cert.CertificateException: Certificate has been denied
at com.sun.deploy.security.X509ExtendedDeployTrustManager.checkServerTrusted(X509ExtendedDeployTrustManager.java:336)
at com.sun.net.ssl.internal.ssl.ClientHandshaker.serverCertificate(ClientHandshaker.java:1053)
... 23 more
Exception: java.lang.ClassNotFoundException: com.realobjects.eop.japplet.SwingEditorApplet
------------------------------------------------------------------------------------------------------------------------------------------------------

Sorry for the Huuuuuuuuuuuge post.
Thank you again.

---

### Post by nik16v on 2010-09-09
The above Java problem solved when i putted an exception to Firefox for the url of the program we use at work.
After that works perfectly.

Now the second part.
We use HP smart card Keyboard (and our smart card) to sign the documents.
In XP we have RSA program. What should i do now to work my smart card in ubuntu 10.04
Does HP keyboard need drivers for smart cards?
What should i do?
And i have a MS Access program that i use. Doesn't work in Open Office 3.2. Tried to link the database but nothing happened. 
Any thoughts about that?

Thank you all again!

---

