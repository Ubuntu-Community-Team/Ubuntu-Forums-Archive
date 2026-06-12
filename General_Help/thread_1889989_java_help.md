---
title: "java help"
date: 2011-12-02
forum: General Help
---

### Post by filly on 2011-12-02
When I check my Java installation I get the error below.Java Plug-in 1.6.0_29
      Using JRE version 1.6.0_29-b11 Java HotSpot(TM) Client VM
      User home directory = C:\Users\Cheryl
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
      security: property package.definition new value       com.sun.javaws,com.sun.deploy
      security: property package.definition value       com.sun.javaws,com.sun.deploy
      security: property package.definition new value       com.sun.javaws,com.sun.deploy,com.sun.jnlp
      security: property package.access value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws,com.sun.deploy,com.sun.jnlp
      security: property package.access new value sun.,com.sun.xml.internal.ws.,com.sun.xml.internal.bind.,com.sun.imageio.,com.sun.javaws,com.sun.deploy,com.sun.jnlp,org.mozilla.jss
      security: property package.definition value       com.sun.javaws,com.sun.deploy,com.sun.jnlp
      security: property package.definition new value       com.sun.javaws,com.sun.deploy,com.sun.jnlp,org.mozilla.jss
      basic: Added progress listener:       sun.plugin.util.GrayBoxPainter$GrayBoxProgressListener@19616c7
      network: Cache entry not found [url: [http://java.com/jsp_utils/](http://java.com/jsp_utils/),       version: null]
      network: Cache entry not found [url:       [http://java.com/jsp_utils/jreCheck.class](http://java.com/jsp_utils/jreCheck.class), version: null]
      network: Connecting [http://java.com/jsp_utils/jreCheck.class](http://java.com/jsp_utils/jreCheck.class) with       proxy=DIRECT
      network: Cache entry not found [url:       [http://java.com/jsp_utils/jreCheck/class.class](http://java.com/jsp_utils/jreCheck/class.class), version: null]
      network: Connecting [http://java.com/jsp_utils/jreCheck/class.class](http://java.com/jsp_utils/jreCheck/class.class)       with proxy=DIRECT
      basic: load: class jreCheck.class not found.
      load: class jreCheck.class not found.
      java.lang.ClassNotFoundException: jreCheck.class
          at sun.plugin2.applet.Applet2ClassLoader.findClass(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass0(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass(Unknown       Source)
          at java.lang.ClassLoader.loadClass(Unknown Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Unknown       Source)
          at sun.plugin2.applet.Plugin2Manager.createApplet(Unknown       Source)
          at       sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown       Source)
          at java.lang.Thread.run(Unknown Source)
      Exception: java.lang.ClassNotFoundException: jreCheck.class
      Ignored exception: java.lang.ClassNotFoundException:       jreCheck.class
      basic: Added progress listener:       sun.plugin.util.GrayBoxPainter$GrayBoxProgressListener@191d8c1
      network: Cache entry not found [url:       [http://java.com/jsp_utils/jreVerify.class](http://java.com/jsp_utils/jreVerify.class), version: null]
      network: Connecting [http://java.com/jsp_utils/jreVerify.class](http://java.com/jsp_utils/jreVerify.class) with       proxy=DIRECT
      network: Cache entry not found [url:       [http://java.com/jsp_utils/jreVerify/class.class](http://java.com/jsp_utils/jreVerify/class.class), version: null]
      network: Connecting       [http://java.com/jsp_utils/jreVerify/class.class](http://java.com/jsp_utils/jreVerify/class.class) with proxy=DIRECT
      basic: load: class jreVerify.class not found.
      load: class jreVerify.class not found.
      java.lang.ClassNotFoundException: jreVerify.class
          at sun.plugin2.applet.Applet2ClassLoader.findClass(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass0(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass(Unknown       Source)
          at java.lang.ClassLoader.loadClass(Unknown Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Unknown       Source)
          at sun.plugin2.applet.Plugin2Manager.createApplet(Unknown       Source)
          at       sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown       Source)
          at java.lang.Thread.run(Unknown Source)
      Exception: java.lang.ClassNotFoundException: jreVerify.class
      Ignored exception: java.lang.ClassNotFoundException:       jreVerify.class
      basic: Added progress listener:       sun.plugin.util.GrayBoxPainter$GrayBoxProgressListener@1c92535
      basic: Plugin2ClassLoader.addURL parent called for       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar)
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Connecting [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar) with       proxy=DIRECT
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Connecting [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar) with       proxy=DIRECT
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Connecting [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar) with       proxy=DIRECT
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Connecting [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar) with       proxy=DIRECT
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Connecting [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar) with       proxy=DIRECT
      network: Cache entry not found [url:       [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar), version: null]
      network: Connecting [http://java.com/applet/TestVM2-test.jar](http://java.com/applet/TestVM2-test.jar) with       proxy=DIRECT
      network: Cache entry not found [url: [http://java.com/applet/](http://java.com/applet/),       version: null]
      network: Cache entry not found [url:       [http://java.com/applet/testJava2_1/TestVMApplet.class](http://java.com/applet/testJava2_1/TestVMApplet.class), version:       null]
      network: Connecting       [http://java.com/applet/testJava2_1/TestVMApplet.class](http://java.com/applet/testJava2_1/TestVMApplet.class) with       proxy=DIRECT
      network: Cache entry not found [url:       [http://java.com/applet/testJava2_1/TestVMApplet/class.class](http://java.com/applet/testJava2_1/TestVMApplet/class.class),       version: null]
      network: Connecting       [http://java.com/applet/testJava2_1/TestVMApplet/class.class](http://java.com/applet/testJava2_1/TestVMApplet/class.class) with       proxy=DIRECT
      basic: load: class testJava2_1/TestVMApplet.class not found.
      load: class testJava2_1/TestVMApplet.class not found.
      java.lang.ClassNotFoundException: testJava2_1.TestVMApplet.class
          at sun.plugin2.applet.Applet2ClassLoader.findClass(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass0(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass(Unknown       Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadClass(Unknown       Source)
          at java.lang.ClassLoader.loadClass(Unknown Source)
          at sun.plugin2.applet.Plugin2ClassLoader.loadCode(Unknown       Source)
          at sun.plugin2.applet.Plugin2Manager.createApplet(Unknown       Source)
          at       sun.plugin2.applet.Plugin2Manager$AppletExecutionRunnable.run(Unknown       Source)
          at java.lang.Thread.run(Unknown Source)
      Exception: java.lang.ClassNotFoundException:       testJava2_1.TestVMApplet.class
      Ignored exception: java.lang.ClassNotFoundException:       testJava2_1.TestVMApplet.class
      security: Accessing keys and certificate in Mozilla user profile:       null

---

### Post by ratcheer on 2011-12-02
I have been looking at Java all day, too. I successfully installed openjdk-7-jre, but that still did not configure a browser plugin.

I want to install Oracle Java 7, but the instructions are daunting. I have manually installed it before, and it worked satisfactorily, but I never got the installation completely correct for all the "alternatives".

We really need a guide for correctly and completely installing Java.

Tim

---

### Post by ratcheer on 2011-12-02
I got it installed and working. See posts 52 and 53 in this thread.

[http://ubuntuforums.org/showthread.php?t=422692&page=6](http://ubuntuforums.org/showthread.php?t=422692&page=6)

Tim

---

