---
title: "Java Browser Games"
date: 2010-10-27
forum: General Help
---

### Post by elohssa on 2010-10-27
For some reason when I try to load Java games in the browser they fail to load and the screen stays gray for a few seconds and then the window closes and I am taken to the error page for that website.  Any ideas or suggestions?  I am running Ubuntu 10.10.

Thanks

---

### Post by P4man on 2010-10-28
Sorry to ask the obvious, but do you have java installed? Go to the software center and make sure you have "OpenJDK Java 6" and IcedTea installed. If thats already the case, please give us an example of a java game thats not working.

---

### Post by slooksterpsv on 2011-01-25
Do the following, this will tell us if you're using OpenJDK or Sun (Oracle) Java:

Click Applications -> Accessories -> Terminal

Type the following and press enter:

```

update-alternatives --config java

```

EDIT: Paste the results back here. I want to assume its due to not having sun java or not having sun java set

---

### Post by jivana on 2011-01-26
> **P4man said:**
> Sorry to ask the obvious, but do you have java installed? Go to the software center and make sure you have "OpenJDK Java 6" and IcedTea installed. If thats already the case, please give us an example of a java game thats not working.

Experiencing a similar problem, where in [http://www.bundesliga.de/de/manager/index.php](http://www.bundesliga.de/de/manager/index.php), after logging in, click **Hier geht's zum Spiel** and then there is a link to **Stadion**, which starts the simulation of the football game your team played (it's a football manager game). 
They recommend to have just Sun Java installed, which i have ("There is only one alternative in link group java: /usr/lib/jvm/java-6-sun/jre/bin/java
Nothing to configure."); however, on my computer, the starting of the Java applet hangs eventually. 
The Java console reports:
basic: Plugin2ClassLoader.getPermissions CeilingPolicy allPerms
network: Connecting [http://www.aitcloud.de/ws/aitws/request?USER_ID=11177&SESSION=I11177DQNC56G2CBJVTPM0ZP7UH40336&DB=bundesliga_de&cmd=load_settings](http://www.aitcloud.de/ws/aitws/request?USER_ID=11177&SESSION=I11177DQNC56G2CBJVTPM0ZP7UH40336&DB=bundesliga_de&cmd=load_settings) with proxy=DIRECT
network: Connecting [http://www.aitcloud.de/ws/aitws/request?USER_ID=11177&SESSION=I11177DQNC56G2CBJVTPM0ZP7UH40336&DB=bundesliga_de&cmd=load_settings](http://www.aitcloud.de/ws/aitws/request?USER_ID=11177&SESSION=I11177DQNC56G2CBJVTPM0ZP7UH40336&DB=bundesliga_de&cmd=load_settings) with cookie "PHPSESSID=622477b9b7f1f14f9c9cb863f396feb3"
Default Display could not be created! Using Software Renderer.
org.lwjgl.LWJGLException: X Error - disp: 0x87ce1d8 serial: 148 error: BadGC (invalid GC parameter) request_code: 60 minor_code: 0
	at org.lwjgl.opengl.LinuxDisplay.globalErrorHandler(LinuxDisplay.java:276)
	at org.lwjgl.opengl.LinuxKeyboard.nSetDetectableKeyRepeat(Native Method)
	at org.lwjgl.opengl.LinuxKeyboard.setDetectableKeyRepeat(LinuxKeyboard.java:152)
	at org.lwjgl.opengl.LinuxKeyboard.destroy(LinuxKeyboard.java:163)
	at org.lwjgl.opengl.LinuxDisplay.destroyKeyboard(LinuxDisplay.java:1054)
	at org.lwjgl.input.Keyboard.destroy(Keyboard.java:349)
	at org.lwjgl.opengl.Display.destroyWindow(Display.java:357)
	at org.lwjgl.opengl.Display.access$300(Display.java:67)
	at org.lwjgl.opengl.Display$3.destroy(Display.java:146)
	at org.lwjgl.opengl.Display.create(Display.java:864)
	at org.lwjgl.opengl.Display.create(Display.java:785)
	at org.lwjgl.opengl.Display.create(Display.java:766)
	at P.D.A(Unknown Source)
	at engine.D.C(Unknown Source)
	at M.B.H(Unknown Source)
	at engine.B$_A.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:662)
(null:-1): java.lang.NullPointerException
	at org.lwjgl.opengl.GL11.glGetString(GL11.java:1771)
	at R.A.D.<init>(Unknown Source)
	at R.A.B.E(Unknown Source)
	at M.B.H(Unknown Source)
	at engine.B$_A.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:662)

Exception in thread "CoronaGameThread" java.lang.NullPointerException
	at org.lwjgl.opengl.GL11.glGenTextures(GL11.java:1372)
	at I.D.Ó(Unknown Source)
	at I.D.N(Unknown Source)
	at F.A.G.E(Unknown Source)
	at F.A.G.B(Unknown Source)
	at I.E.<init>(Unknown Source)
	at engine.H.G(Unknown Source)
	at M.B.H(Unknown Source)
	at engine.B$_A.run(Unknown Source)
	at java.lang.Thread.run(Thread.java:662)

Would be awesome if someone was able to help on this, thanks!

---

