---
title: "HTTP webcam-server = java error"
date: 2010-02-15
forum: General Help
---

### Post by SlugSlug on 2010-02-15
Hi All,

I have followed instructions here [http://www.linuxsolutions.fr/how-to-set-up-an-ubuntu-webcam-server/](http://www.linuxsolutions.fr/how-to-set-up-an-ubuntu-webcam-server/)

to install apache and webcam-server 

[http://localhost:8888](http://localhost:8888) shows my cam but the [http://localhost/webcam.html](http://localhost/webcam.html) loads a java app and then crashes with

Java Plug-in 1.6.0_18
Using JRE version 1.6.0_18-b07 Java HotSpot(TM) Client VM
User home directory = C:\Documents and Settings\Administrator
----------------------------------------------------
c:   clear console window
f:   finalize objects on finalization queue
g:   garbage collect
h:   display this help message
l:   dump classloader list
m:   print memory usage
o:   trigger logging
q:   hide console
r:   reload policy configuration
s:   dump system and deployment properties
t:   dump thread list
v:   dump thread stack
x:   clear classloader cache
0-5: set trace level to <n>
----------------------------------------------------


load: class WebCamApplet.class not found.
java.lang.ClassNotFoundException: WebCamApplet.class
    at sun.plugin2.applet.Applet2ClassLoader.findClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at java.lang.ClassLoader.loadClass(Unknown Source)
    at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Unknown Source)
    at sun.plugin2.applet.Plugin2Manager.createApplet(Unknown Source)
    at sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown Source)
    at java.lang.Thread.run(Unknown Source)
Caused by: java.net.ConnectException: Connection refused: connect
    at java.net.PlainSocketImpl.socketConnect(Native Method)
    at java.net.PlainSocketImpl.doConnect(Unknown Source)
    at java.net.PlainSocketImpl.connectToAddress(Unknown Source)
    at java.net.PlainSocketImpl.connect(Unknown Source)
    at java.net.SocksSocketImpl.connect(Unknown Source)
    at java.net.Socket.connect(Unknown Source)
    at sun.net.NetworkClient.doConnect(Unknown Source)
    at sun.net.[www.http.HttpClient.openServer(Unknown](www.http.HttpClient.openServer(Unknown) Source)
    at sun.net.[www.http.HttpClient.openServer(Unknown](www.http.HttpClient.openServer(Unknown) Source)
    at sun.net.www.http.HttpClient.<init>(Unknown Source)
    at sun.net.[www.http.HttpClient.New(Unknown](www.http.HttpClient.New(Unknown) Source)
    at sun.net.[www.http.HttpClient.New(Unknown](www.http.HttpClient.New(Unknown) Source)
    at sun.net.[www.protocol.http.HttpURLConnection.getNewHttpClient(Unknown](www.protocol.http.HttpURLConnection.getNewHttpClient(Unknown) Source)
    at sun.net.[www.protocol.http.HttpURLConnection.plainConnect(Unknown](www.protocol.http.HttpURLConnection.plainConnect(Unknown) Source)
    at sun.net.[www.protocol.http.HttpURLConnection.connect(Unknown](www.protocol.http.HttpURLConnection.connect(Unknown) Source)
    at sun.net.[www.protocol.http.HttpURLConnection.getInputStream(Unknown](www.protocol.http.HttpURLConnection.getInputStream(Unknown) Source)
    at java.net.HttpURLConnection.getResponseCode(Unknown Source)
    at sun.plugin2.applet.Applet2ClassLoader.getBytes(Unknown Source)
    at sun.plugin2.applet.Applet2ClassLoader.access$000(Unknown Source)
    at sun.plugin2.applet.Applet2ClassLoader$1.run(Unknown Source)
    at java.security.AccessController.doPrivileged(Native Method)
    ... 7 more
Exception: java.lang.ClassNotFoundException: WebCamApplet.class


Anyone know why / how to fix?

---

