---
title: "Firefox 1.5 Java JRE 1.5 sorta almost half works?"
date: 2006-03-31
forum: General Help
---

### Post by burgundy on 2006-03-31
I'm currently using this page as a test for my Java JRE plugin for Firefox:
[https://jogl-demos.dev.java.net/applettest.html](https://jogl-demos.dev.java.net/applettest.html)

If everything is set up correctly, the applet should ask me to authenticate/allow it to run and  load with no other questions.

Well I've messed around with Firefox 1.0.7 and 1.5 and Java 1.4.2 and Java 1.5.  This applet has never worked on my Ubuntu box.

It asks me to authenticate the applet, loads the white box, and just sits/hangs at "Starting applet JOGL Gears Applet".

Could there be a possible write permission error that isn't being reported?  I know the applet is downloading and executing something from somewhere, but maybe Ubuntu doesn't like where/how it is doing this?

I'm very new to Ubuntu, so I don't fully understand 'the way' permissions are expected to work.

Every other Java applet I've found to test the JRE has worked.

This official page works fine: [http://www.java.com/en/download/help/testvm.xml](http://www.java.com/en/download/help/testvm.xml)

Stuff like Azureus and the Eclipse IDE work fine, but for whatever reason, this applet doesn't like the way I've set up my Ubuntu.

I'm afraid that the JRE 1.4 and JRE 1.5 are mixed up somehow, so any fool proof links to tutorials on how to  uninstall/reinstall/make sure your Ubuntu Firefox and JRE are 1.5 and absolutely fully functional would be useful.

java --version says 1.5.0_06-b05

my /opt/firefox/plugin is linked to /usr/lib/j2re1.5-sun/plugin/i386/ns7/libjavaplugin_oji.so

Other than that plugin link, what else would firefox need?

I've been following this tutorial:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

and this one:
[http://www.docuverse.com/blog/donpark/EntryViewPage.aspx?guid=f171bafc-abce-4d2e-a18b-3aba4ad32c52](http://www.docuverse.com/blog/donpark/EntryViewPage.aspx?guid=f171bafc-abce-4d2e-a18b-3aba4ad32c52)

---

### Post by testube_babies on 2006-03-31
are you sure that when you open firefox you are opening the version in /opt/?

try opening a terminal and typing '/opt/firefox/firefox'

i apologize in advance if this doesn't work ;).  but hey, it's worth a shot.

---

### Post by burgundy on 2006-04-01
Ya, that isn't the problem. :)

---

### Post by burgundy on 2006-04-04
Well I've tried

sudo chown -R ${USER}:${USER} /opt/firefox

and attempted to run the applet, and it still fails to fully execute and gets stuck in the loading phase.

I recently installed Opera to test my JRE.  Well the applet installed and loaded correctly on the first try, but since that first load, it doesn't work anymore and acts just like Firefox, which I suspect did the same thing (load correctly on the first try, and has broken since then).

For whatever reason both browsers now sit at "Starting applet JOGL Gears Applet".

Does this at least confirm there is something wrong with my JRE and not with how the browsers are configured?

---

### Post by burgundy on 2006-04-05
Well I did a 'sudo dpkg -r' in an attempt to completely remove my current JRE and try again... nothing has changed.

I have crashed both Firefox and Opera by hitting the refresh button one too many times while the applet is supposedly 'starting'.

It is very strange how during this process it has worked and stopped working multiple times, but I've only seen it work through my VNC connection, never when I'm actually sitting at the computer's monitors... hopefully the JRE doesn't care whether I'm looking at the OpenGL applet through a TwinView setup or VNC server.

---

### Post by burgundy on 2006-04-05
ok... well a dug around for the 'java web start' utility, changed some config options and told the debugger console to pop.  When trying to run the JOGL applet this stuff happens:

network: Connecting [http://download.java.net/media/jogl/builds/archive/jsr-231-webstart-current/jogl-demos.jar](http://download.java.net/media/jogl/builds/archive/jsr-231-webstart-current/jogl-demos.jar) with cookie " "
basic: Loading [http://download.java.net/media/jogl/builds/archive/jsr-231-webstart-current/jogl-demos.jar](http://download.java.net/media/jogl/builds/archive/jsr-231-webstart-current/jogl-demos.jar) from cache
basic: No certificate info, this is unsigned JAR file.
network: Connecting [http://download.java.net/media/jogl/builds/archive/jsr-231-webstart-current/jogl-natives-linux.jar](http://download.java.net/media/jogl/builds/archive/jsr-231-webstart-current/jogl-natives-linux.jar) with proxy=DIRECT
network: Connecting [http://download.java.net/media/jogl/builds/archive/jsr-231-webstart-current/jogl-natives-linux.jar](http://download.java.net/media/jogl/builds/archive/jsr-231-webstart-current/jogl-natives-linux.jar) with cookie " "
Beginning DRI hack
Exception in thread "AWT-EventQueue-2" java.lang.UnsatisfiedLinkError: dlopen
	at com.sun.opengl.impl.x11.DRIHack.dlopen(Native Method)
	at com.sun.opengl.impl.x11.DRIHack.begin(DRIHack.java:98)
	at com.sun.opengl.impl.x11.X11GLDrawableFactory.<clinit>(X11GLDrawableFactory.java:61)
	at java.lang.Class.forName0(Native Method)
	at java.lang.Class.forName(Class.java:164)
	at javax.media.opengl.GLDrawableFactory.getFactory(GLDrawableFactory.java:111)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:113)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:82)
	at javax.media.opengl.GLCanvas.<init>(GLCanvas.java:75)
	at demos.applets.GearsApplet.init(GearsApplet.java:19)
	at com.sun.opengl.util.JOGLAppletLauncher.startSubApplet(JOGLAppletLauncher.java:711)
	at com.sun.opengl.util.JOGLAppletLauncher.access$700(JOGLAppletLauncher.java:117)
	at com.sun.opengl.util.JOGLAppletLauncher$2.run(JOGLAppletLauncher.java:675)
	at java.awt.event.InvocationEvent.dispatch(InvocationEvent.java:209)
	at java.awt.EventQueue.dispatchEvent(EventQueue.java:461)
	at java.awt.EventDispatchThread.pumpOneEventForHierarchy(EventDispatchThread.java:242)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(EventDispatchThread.java:163)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:157)
	at java.awt.EventDispatchThread.pumpEvents(EventDispatchThread.java:149)
	at java.awt.EventDispatchThread.run(EventDispatchThread.java:110)


AND

General Exception

java.lang.NullPointerException
  at demos.applets.GearsApplet.stop(GearsApplet.java:32)
  at com.sun.opengl.util.JOGLAppletLauncher.stop(JOGLAppletLauncher.java:322)
  at sun.applet.AppletPanel.run(AppletPanel.java:479)
  at java.lang.Thread.run(Thread.java:595)

These look like real errors.  Errors that I don't get on my windows machines.  Should I keep asking about this in the Ubuntu Forums or ask elsewhere, possibly more Java centric?

---

### Post by burgundy on 2006-04-05
oh, and I switched to the full JDK instead of just the JRE.

---

