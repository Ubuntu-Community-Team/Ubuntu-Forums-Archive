---
title: "Natty and Java"
date: 2011-09-29
forum: General Help
---

### Post by rogue1987 on 2011-09-29
I can't seem to get Java to run in either Chrome or Firefox. I have a webinar site that I need to go to. Page extension is .jnlp and both browsers just want to download it, rather than launch the app.

I've installed java, uninstalled, re-installed, tried this that and the other thing I've found on the web and just can't seem to make it go. Where do I go from here?

32-bit 11.04 by the way...

---

### Post by rogue1987 on 2011-09-30
wow, no one has anything on this?

---

### Post by PayPaul on 2011-10-01
I have the same problem. It only showed up today on the Flickr website. I tried to go to someones main photostream page and get text only. The text is all scrambled on top of itself and the error message clearly shows that Java is not enabled. I looked at my plugins list and Java JRE is not even listed. I never seemed to have the problem before today. Now I see that Java requires a much more complicated install than before. How come the Firefox linux version doesn't self install it? It seems to require command lines just like a lot of other Linux programs. It also requires going through some hoops at the Oracle site. Before on Windows based FF the plugin installed from the browser. Most other vital plugins still install from the Linux version but for this one.

Update: Checked other contacts photostream pages and they work fine. It might be a site issue not a plugin issue. Yet I do not see an entry in FF for Java nonetheless and I don't even know which version to install.

---

### Post by kanishkdudeja on 2011-10-01
had the same problem dude..

only worked under internet explorer in windows..

---

### Post by rogue1987 on 2011-10-01
> **kanishkdudeja said:**
> had the same problem dude..

only worked under internet explorer in windows..
but i don't want to use IE in Windows...

---

### Post by cameronedwards on 2011-10-01
Try to use the website with Midori. I had a problem with flash loading, -BBC iplayer stuff- and Midori fixed that.

---

### Post by PayPaul on 2011-10-01
> **cameronedwards said:**
> Try to use the website with Midori. I had a problem with flash loading, -BBC iplayer stuff- and Midori fixed that.

Does Midori support porting personal settings from other browsers? I'll look into it. As of now I'm only using Firefox.

---

### Post by rogue1987 on 2011-10-01
> **cameronedwards said:**
> Try to use the website with Midori. I had a problem with flash loading, -BBC iplayer stuff- and Midori fixed that.

But I'm not having a Flash problem, I'm having a Java problem.

---

### Post by jasonread on 2011-10-06
Hi, I am having a related issue. Upgrades from 10.04 to 11.04 over the last couple of days and everything but the ability to run jnlps seems to have survived intact. I had to use some workarounds in 10.04 but they don't seem to be working at the moment. I did some googling and have tried starting the jnlp using icedtea java 6 webstart, Sun Java 6 webstart and Sun Java 6 webstart (32 bit) (FYI I am running 64 bit). The jnlp I am trying to run only works with JRE 1.5, which is tried to download and install each run. Thinking this might have been the issue, I installed JRE 1.5.0.22 and set Java 5 as the default. No dice. 

Here is the jnlp exception I get trying to run. Not sure if this is helpful: 

JNLPException[category: Launch File Error : Exception: null : LaunchDesc: 
<jnlp spec="1.0+" codebase="http://javadl.sun.com/webapps/jawsautodl/AutoDL/j2se/">
  <information>
    <title>J2RE 1.5.0_22 Installer</title>
    <vendor>Sun Microsystems, Inc.</vendor>
    <homepage href="null"/>
  </information>
  <security>
    <all-permissions/>
  </security>
  <update check="timeout" policy="always"/>
  <resources>
    <java href="http://java.sun.com/products/autodl/j2se" version="1.3+"/>
    <jar href="http://javadl.sun.com/webapps/jawsautodl/AutoDL/j2se/javaws-j2re-inst.jar" download="eager" main="false"/>
    <property name="installerLocation" value="jre-1_5_0_22-linux-i586.bin"/>
    <property name="installerSize" value="17283082"/>
    <property name="javaVersion" value="1.5.0_22"/>
    <property name="platformVersion" value="1.5"/>
    <property name="licenseSize" value="13238"/>
    <property name="waitString.0" value="[yes or no]"/>
    <property name="responseString.0" value="yes"/>
    <property name="osplatform" value="linux-i586"/>
  </resources>
  <installer-desc main-class="com.sun.webstart.installers.Main"/>
</jnlp> ]
	at com.sun.javaws.JnlpxArgs.executeInstallers(JnlpxArgs.java:500)
	at com.sun.javaws.Launcher.prepareResources(Launcher.java:993)
	at com.sun.javaws.Launcher.prepareAllResources(Launcher.java:621)
	at com.sun.javaws.Launcher.prepareToLaunch(Launcher.java:327)
	at com.sun.javaws.Launcher.prepareToLaunch(Launcher.java:199)
	at com.sun.javaws.Launcher.launch(Launcher.java:116)
	at com.sun.javaws.Main.launchApp(Main.java:416)
	at com.sun.javaws.Main.continueInSecureThread(Main.java:248)
	at com.sun.javaws.Main$1.run(Main.java:110)
	at java.lang.Thread.run(Thread.java:662)


Any ideas would be very appreciated at this point. I need this for work and really don't want to have to boot into windows for it.

Thanks....

---

