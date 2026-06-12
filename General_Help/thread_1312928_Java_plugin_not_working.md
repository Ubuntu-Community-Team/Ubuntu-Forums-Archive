---
title: "Java plugin not working"
date: 2009-11-03
forum: General Help
---

### Post by sugarat on 2009-11-03
Hi All, 
 Very impressed with 9.10 so far, but one issue which is bugging me... I have installed the Java6 jre and plugin, but when I go onto FaceBook and it goes to load the Java photo uploader, it seems to half load it and then stop.  I get a blank grey window and nothing else happens. 

 Any ideas?

---

### Post by Mighty_Joe on 2009-11-03
> **sugarat said:**
> I have installed the Java6 jre and plugin, but when I go onto FaceBook and it goes to load the Java photo uploader, it seems to half load it and then stop.  

So Java is working.  A particular Java application is not.  Correct?
What is the output of "update-java-alternatives -l"
What do you see if you visit [this page?]("java.com/en/download/installed.jsp")

---

### Post by sugarat on 2009-11-03
Output is:

```

java-6-sun 63 /usr/lib/jvm/java-6-sun

```

The web page says:

```

Oops! You don't have the recommended Java installed.
Your Java version is Version 6 Update 15. Please click the button below to get the recommended Java for your computer.

NOTE: If you recently completed your Java software installation, you may need to restart your browser (close all browser windows and re-open) before verifying your installation.

```

---

### Post by scouser73 on 2009-11-03
This site shows how to install Sun Java, an independent way rather then via Synaptic Package Manager: [[COLOR="Red"]**Install Sun Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by sugarat on 2009-11-03
Okay so I downloaded the Java plugin and am now using that from ~/.mozilla/plugins but the behaviour is the same. Don't get it...

The Facebook photo app works on Windows & Mac and I've had it working on Linux before.. just seems to be this install it started not working. :(

Hmm what else can I try? This is vanilla 9.10 karmic fresh install. 

Thanks for your help.

---

### Post by Mighty_Joe on 2009-11-03
> **scouser73 said:**
> This site shows how to install Sun Java, an independent way rather then via Synaptic Package Manager: [[COLOR="Red"]**Install Sun Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

Personally, I'd stay with what's in the repositories.  If one installs Java manually, one has to keep up with all the updates going forward manually.

@sugarat: Have you tried uploading other images?  I can't get to Facebook right now to test the uploader myself.

---

### Post by jms-ubuntu-en on 2009-11-04
Yes, the best solution for the brand new karmic and it's overall functionality would be to stick with the supplies of the repositories... 
But Sun's Java {JDK,JRE} 6 update 16 and prior have vulnerabilities which are rated as critical:
[http://www.vupen.com/english/advisories/2009/3131](http://www.vupen.com/english/advisories/2009/3131)

---

### Post by nacholand on 2009-11-05
Hi there guys!

I found the solution (that some actually posted in these forums)

You need to reinstall it manually downloading the Java 6 SE update 17 from the java.sun site
I just did it and now I got it working just fine

Link with info here:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Hope it helps! (if it didn't already)

---

### Post by sugarat on 2009-11-05
Thanks Nacholand.. I will give it a go!

---

### Post by QIII on 2009-11-05
> **Mighty_Joe said:**
> Personally, I'd stay with what's in the repositories.  If one installs Java manually, one has to keep up with all the updates going forward manually.

@sugarat: Have you tried uploading other images?  I can't get to Facebook right now to test the uploader myself.

Canonical has decided to go with OpenJDK from Karmic forward, and likely will not be providing security updates to Java in any case.

My suggestion is to follow this guy's instructions.  He has already updated his blog to update 17:

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Edit:  Eh.  I see it above, now.  Never mind.

---

### Post by sugarat on 2009-11-05
This is weird.  Instructions followed.. Java plugin correctly displayed by Firefox (about:plugins) and java.com website confirms Jre 6u17 installed. 

Facebook photos app.... still no joy. Crashes Firefox.  What the frig..

---

### Post by scouser73 on 2009-11-05
Try this - [[COLOR="Red"]**Install Java**[/COLOR]]("http://sites.google.com/site/easylinuxtipsproject/java")

It's extremely easy to follow.

---

### Post by Soul-Sing on 2009-11-05
> **sugarat said:**
> This is weird.  Instructions followed.. Java plugin correctly displayed by Firefox (about:plugins) and java.com website confirms Jre 6u17 installed. 

Facebook photos app.... still no joy. Crashes Firefox.  What the frig..

these instructions from pjotr123 rawks. when you do the browser-plugin  part of this geat howto, please close firefox.
after that create a symlink in/to the plugin folder.

---

### Post by sugarat on 2009-11-06
I've done all of the instructions but the it's not working.  Firefox just greys out and dies when trying to load a Java plugin

---

### Post by QIII on 2009-11-06
What happens when you go to the Sun website and test your plugin?

---

### Post by sugarat on 2009-11-06
Well this is strange. I went back to the desktop Firefox was on and it seemed to be working!

Further experimentation after reloading Firefox shows that it seems to hang Firefox for a while before eventually appearing..  A step in the right direction though!

I will have a play and see if it's any faster when I try and upload photos.. 

Thanks

---

### Post by sugarat on 2009-11-06
Nope.  Just tried it again and Firefox is hung.  100% CPU usage between Firefox and java_vm process. 

So I just installed Opera as an experiment. The Java.com website confirms I have Java installed, but the Facebook page says 'Loading Applet', and then 'Applet not found' after a while. Whilst it's tempting to have a go at Facebook, it works perfectly on my Windows install, so I would still like to know what Ubuntu is having a problem with.

---

### Post by knattlhuber on 2009-11-07
Similar problem here: Vanilla Karmic install and java-based web application (eClass) not displaying content properly.

Java 1.6.15 is installed and running (as per the Java test page). I haven't tried the suggested solution posted earlier in this thread as the eClass application only requires Java 2, so I don't see the use of upgrading to 6.17. The site has been working fine for me under Firefox before.

---

### Post by DougieFresh4U on 2009-11-07
Java installed here but Frostwire won't recognize it, using Karmic:
```

java.lang.NoClassDefFoundError: org/limewire/util/VersionUtils
	at com.limegroup.gnutella.gui.GUILoader.load(Unknown Source)
	at sun.reflect.NativeMethodAccessorImpl.invoke0(Native Method)
	at sun.reflect.NativeMethodAccessorImpl.invoke(NativeMethodAccessorImpl.java:57)
	at sun.reflect.DelegatingMethodAccessorImpl.invoke(DelegatingMethodAccessorImpl.java:43)
	at java.lang.reflect.Method.invoke(Method.java:616)
	at com.limegroup.gnutella.gui.Main.main(Unknown Source)
Caused by: java.lang.ClassNotFoundException: org.limewire.util.VersionUtils
	at java.net.URLClassLoader$1.run(URLClassLoader.java:217)
	at java.security.AccessController.doPrivileged(Native Method)
	at java.net.URLClassLoader.findClass(URLClassLoader.java:205)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:323)
	at sun.misc.Launcher$AppClassLoader.loadClass(Launcher.java:294)
	at java.lang.ClassLoader.loadClass(ClassLoader.java:268)
	... 6 more

STARTUP ERROR!
```

---

### Post by soma1509 on 2009-11-07
Hey guys, I am having the same problem.

I already have the latest Java version  6u17
It is properly detected on Java.com
I already have the latest Java plugin for firefox and it works fine loading other applets, such as the games from pogo.com
I also tried this on firefox 3.5.4 (the one included with Ubuntu 9.10) and also firefox 3.5.5 (the latest available) from the main download page at mozilla.com
Java works on both versions and already checked under about : plugins and the plugin is shown there.
The only problem is when facebook grays out my browser when loading its photo uploader applet, though it does not freeze the browser...it just shows a gray box where the uploader is supposed to be. Has anyone found out a solution yet?

Thanks in advance!

---

### Post by Mighty_Joe on 2009-11-09
> **DougieFresh4U said:**
> 
```

java.lang.NoClassDefFoundError: org/limewire/util/VersionUtils

```

I think that's a different problem.  Java's working fine.  Your application can't find a file it needs. How did you install Frostwire? How are you running it?

---

