---
title: "Runescape only safemode"
date: 2010-04-30
forum: General Help
---

### Post by rasmus91 on 2010-04-30
Hi there

As the title suggest im currently only able to run runescape in safemode.

This sucks, as far is i'm concerned it has something to do with 10.04 not running SUN java.

This is the 64 bit version of ubuntu 10.04.

I have currently installed Restricted extras.

If graphics card does any how matter i have a Dell E6400 with GMA 4500 MHD...

Any help will be greatly appreciated.

---

### Post by rasmus91 on 2010-05-03
OKay, i read some place that the best java plugin for runescape is Sunjava

So i added the canonical partner repository, and installed sun java.

This however doesn't help me, it loads runescape faster, but im still only able to run it in safemode.

Anyone playing runescape, or just knowing how to fix this?

---

### Post by rasmus91 on 2010-05-03
Bump.

---

### Post by rasmus91 on 2010-05-03
Okay, so i figured out how to get a lot of information from the Java console. i have no idea what this means, but i'd like if anyone could tell me what to do. This is what happens when i press play in standard detail:

```
Java Plug-in 1.6.0_20
Using JRE version 1.6.0_20-b02 Java HotSpot(TM) 64-Bit Server VM
User home directory = /home/rasmus

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

security: property package.access value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.
security: property package.access new value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws
security: property package.access value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws
security: property package.access new value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws,com.sun.deploy
security: property package.access value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws,com.sun.deploy
security: property package.access new value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws,com.sun.deploy,com.sun.jnlp
security: property package.definition value null
security: property package.definition new value com.sun.javaws
security: property package.definition value com.sun.javaws
security: property package.definition new value com.sun.javaws,com.sun.deploy
security: property package.definition value com.sun.javaws,com.sun.deploy
security: property package.definition new value com.sun.javaws,com.sun.deploy,com.sun.jnlp
security: property package.access value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws,com.sun.deploy,com.sun.jnlp
security: property package.access new value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws,com.sun.deploy,com.sun.jnlp,org.mozilla.jss
security: property package.definition value com.sun.javaws,com.sun.deploy,com.sun.jnlp
security: property package.definition new value com.sun.javaws,com.sun.deploy,com.sun.jnlp,org.mozilla.jss
basic: Added progress listener: sun.plugin.util.GrayBoxPainter$GrayBoxProgressListener@3a289d2e
basic: Plugin2ClassLoader.addURL parent called for http://world120.runescape.com/loader1047980663.jar
security: Blacklist revocation check is enabled
security: Trusted libraries list check is enabled
network: Cache entry found [url: http://world120.runescape.com/loader1047980663.jar, version: null] prevalidated=true/0
cache: Reading Signers from 2051 http://world120.runescape.com/loader1047980663.jar | /home/rasmus/.java/deployment/cache/6.0/41/5a091429-734535a3.idx
cache:  Read manifest for http://world120.runescape.com/loader1047980663.jar: read=870 full=870
basic: Plugin2ClassLoader.getPermissions CeilingPolicy allPerms
basic: Applet loaded.
basic: Applet resized and added to parent container
basic: PERF: AppletExecutionRunnable - applet.init() BEGIN ; jvmLaunch dt 103796 us, pluginInit dt 1003638 us, TotalTime: 1107434 us
basic: Applet initialized
basic: Removed progress listener: sun.plugin.util.GrayBoxPainter$GrayBoxProgressListener@3a289d2e
basic: Applet made visible
basic: Starting applet
basic: completed perf rollup
basic: Applet started
basic: Told clients applet is started
network: Connecting http://world120.runescape.com:43594/ with proxy=DIRECT

```

can anyone tell me what now?

---

### Post by Zirts on 2010-08-18
Having the same problem, help would be apreciated.

---

### Post by Doublex8 on 2010-09-20
I am also having this problem, any help would be greatly appreciated

---

