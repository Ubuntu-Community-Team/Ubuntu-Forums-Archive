---
title: "Site says I don't have Java installed... but I coulda sworn I do..."
date: 2012-08-08
forum: General Help
---

### Post by t0p on 2012-08-08
Running Ubuntu 12.04 (64 bit).  A site, [savemedia.com]("http://savemedia.com"), won't work for me because it says "You do not appear to have java installed on your system".  In previous incarnations of Ubuntu, the command

```
sudo apt-get install ubuntu-restricted-extras
```got me all kinds of goodies, including, I believe, Java, so most web media was available to me.  But the latest Ubuntu *doesn't* include it in ubuntu-restricted-extras?

Can anyone please tell me what's up with this, and what I gotta do?  Cheers.
 
**EDIT:** A search in that "Dash Home" bar got me the result **Sorry, there is nothing that matches your search**.  So, really truly no Java?  What is that all about?  Ubuntu in the past has *always* (as far as I can recall) had Java, or an easy way to get it.

**ANOTHER EDIT:**  Before anyone says "Duh, get it from Software Centre yuh doofus!" - I searched for "java" in the Ubuntu Software Centre and it gave me lotsa results and no clue which one I actually need...  :(

---

### Post by efflandt on 2012-08-08
Apparently ubuntu-restricted-extras no longer installs any java by default, despite what its description says, since you have your choice of openjdk-6-jre or openjdk-7-jre.  I have still been using openjdk-6-jre because that works fine for a java game I play (minecraft).  I think installing either of those might automatically install related browser plugins, but not sure since I haven't used java websites.

```
$ **dpkg-query -l openjdk***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  openjdk-6-dbg  <none>         (no description available)
un  openjdk-6-demo <none>         (no description available)
un  openjdk-6-doc  <none>         (no description available)
un  openjdk-6-jdk  <none>         (no description available)
ii  openjdk-6-jre  6b24-1.11.3-1u OpenJDK Java runtime, using Hotspot JIT
ii  openjdk-6-jre- 6b24-1.11.3-1u OpenJDK Java runtime, using Hotspot JIT (hea
ii  openjdk-6-jre- 6b24-1.11.3-1u OpenJDK Java runtime (architecture independe
un  openjdk-6-jre- <none>         (no description available)
un  openjdk-6-sour <none>         (no description available)
un  openjdk-7-jre  <none>         (no description available)

$ **dpkg-query -l ice***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  iceape-browser <none>         (no description available)
un  iceauth        <none>         (no description available)
un  icedove        <none>         (no description available)
ii  icedtea-6-jre- 6b24-1.11.3-1u Alternative JVM for OpenJDK, using Cacao
ii  icedtea-6-jre- 6b24-1.11.3-1u Alternative JVM for OpenJDK, using JamVM
un  icedtea-6-plug <none>         (no description available)
un  icedtea-gcjweb <none>         (no description available)
ii  icedtea-netx   1.2-2ubuntu1.1 NetX - implementation of the Java Network La
ii  icedtea-netx-c 1.2-2ubuntu1.1 NetX - implementation of the Java Network La
un  icedtea-plugin <none>         (no description available)
un  icedtea6-jre-c <none>         (no description available)
un  iceweasel      <none>         (no description available)
```PS: Maybe installing just the jre does not enable the browser plugin.  I just installed icedtea-6-plugin and after restarting firefox, it shows up as an add-on:

```
$ **dpkg-query -l ice***
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
un  iceape-browser <none>         (no description available)
un  iceauth        <none>         (no description available)
un  icedove        <none>         (no description available)
ii  icedtea-6-jre- 6b24-1.11.3-1u Alternative JVM for OpenJDK, using Cacao
ii  icedtea-6-jre- 6b24-1.11.3-1u Alternative JVM for OpenJDK, using JamVM
ii  icedtea-6-plug 1.2-2ubuntu1.1 web browser plugin based on OpenJDK and Iced
un  icedtea-gcjweb <none>         (no description available)
ii  icedtea-netx   1.2-2ubuntu1.1 NetX - implementation of the Java Network La
ii  icedtea-netx-c 1.2-2ubuntu1.1 NetX - implementation of the Java Network La
un  icedtea-plugin <none>         (no description available)
un  icedtea6-jre-c <none>         (no description available)
un  icedtea6-plugi <none>         (no description available)
un  iceweasel      <none>         (no description available)
```

Or you can try openjdk-7-jre and icedtea-7-plugin

---

### Post by darkapec on 2012-08-08
If you have access to synaptic package manager just do a search for java in there. I have always done it that way just because there are so many different versions and the naming scheme is very long so use apt-get is just not realistic. 

On a side note if you look at javas website ([http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)) you will notice next to the linux distributions on the right it says "you must enable java in your browser after installation," So you may have java installed you just need to enable it via plugins in firefox.

---

### Post by Sachin Sharma on 2012-08-08
> **darkapec said:**
> If you have access to synaptic package manager just do a search for java in there. I have always done it that way just because there are so many different versions and the naming scheme is very long so use apt-get is just not realistic. 

On a side note if you look at javas website ([http://java.com/en/download/manual.jsp](http://java.com/en/download/manual.jsp)) you will notice next to the linux distributions on the right it says "you must enable java in your browser after installation," So you may have java installed you just need to enable it via plugins in firefox.
latest release of Ubuntu doesn't include synaptic package manager

---

### Post by darkapec on 2012-08-08
> **Sachin Sharma said:**
> latest release of Ubuntu doesn't include synaptic package manager

OUCH!!! I was not aware of this... ok then it must have the Ubuntu software center? I am sure Java is located in there... if not you can install the synaptic package manager by searching in the "Ubuntu Software Center" for synaptic.

Let me know whatcha find out. Either way once you install java you will have to enable it in your browser. So make sure that your browser is not the culprit.

**EDIT**: I just reread your post and the answer is simple, install it from the software center... yes there will be lots of results (there always is) you just need to install "OpenJDK Java 6 (or 7) runtime" my laptop only shows java 6 but that is because I am on 11.04 I believe it is on 7 now.

---

### Post by jockyburns on 2012-08-08
I've been having problems with Java, recently. (I use Google Chrome as my default browser) Several sites I go to come up with messages about the Java plugin not being the latest one. Clicking the update plugin tab takes me to the Java download site (load of use that is,,, not) however clicking the "run this time" tab usually starts Java. 
There does seem to be a problem with sites recognising that Linux systems do indeed have the latest version installed and working. I know I do have the latest version of Java (7) installed and running, as well as the latest iced-tea plugins.

---

### Post by t0p on 2012-08-08
It's me again, the OP.  I installed OpenJDK 7 from Software Centre, as advised, and I've restarted the machine, to make sure it's stuck, but I'm *still* getting messages saying I don't have Java installed - and this is not just 1 site doing this.

Can someone please suggest a cure/workaround?  I'm not getting a "run again" option like the previous poster, I'm just getting a "no java - no deal" attitude, like the sites know better than me what I've installed...

For the love of Eris, look!  A terminal command and output:

```

t0p@mars:~$ which java
/usr/bin/java

```

So why am I getting this "no java" crud?  Seriously, I could just... Grrr!!!

---

### Post by QIII on 2012-08-08
Despite the fact that OpenJDK 7 is the reference open source implementation of Oracle Java 7, some of the world does not see it as Java.  If some websites you visit work and others complain, you are probably running into that.

If you go to [www.java.com/en/](www.java.com/en/) you'll find a link that says "Do I have Java?"

Oracle recognizes OpenJDK (Heck!  They actively develop it!) and will tell you what version you have and if it is up to date.

---

### Post by ILMostro7 on 2012-08-29
Seems to be a bug in google-chrome for linux (at least Ubuntu AFAIK):

[https://groups.google.com/a/chromium.org/d/msg/chromium-bugs/X90hRNmiUVE/xznQtVBmgjYJ]("https://groups.google.com/a/chromium.org/d/msg/chromium-bugs/X90hRNmiUVE/xznQtVBmgjYJ")

Comment #42 on issue 137388 by A.V....@gmail.com: Chrome:plugins reports   
latest java is out of date 
[http://code.google.com/p/chromium/issues/detail?id=137388](http://code.google.com/p/chromium/issues/detail?id=137388) 

> Hey, guys 

I found how to fix this one. In   
src/chrome/browser/resources/plugin_metadata/plugins_linux.json latest java   
version is specified as 1.7.0.5. By version comparison rules 1.7.0.5 is   
greater than 1.7.0_05 and 1.7.0_06, so browser thinks that plugin is out of   
date. Just addding 1.7.0_06 to this file fixes the problem. 

Seems there might be some patches available, according to an updated post - (I haven't tried it yet):

> Updates: 
        Status: Fixed 

Comment #43 on issue 137388 by bau...@chromium.org: Chrome:plugins reports   
latest java is out of date 
[http://code.google.com/p/chromium/issues/detail?id=137388](http://code.google.com/p/chromium/issues/detail?id=137388) 

This is actually fixed in [http://crrev.com/151265;](http://crrev.com/151265;) for some reason bugdroid   
didn't pick it up yet. 

For the commenters here, please note that it will take a while before the   
fix will appear on stable. Also, if you're experiencing this on Windows,   
it's most likely issue 133621; they're completely separate. 

---

### Post by Buntu Bunny on 2012-08-29
> **QIII said:**
> 
If you go to [www.java.com/en/](www.java.com/en/) you'll find a link that says "Do I have Java?"

Well, thanks for this and the discussion in general. I have similar problems and needed answers too. 

I *do* have Synaptic. I installed 12.04 about 3 weeks ago so I'm not sure which latest release Sachin Sharma is referring too. I reckon 12.04.1? Seems odd they would remove it. OTOH, I'm probably behind as usual.

---

### Post by Buntu Bunny on 2012-08-29
Via Synaptic I discovered I already had openjdk-7-jre installed. Thanks to this thread, I knew I had to enable it for my browser (Chrome). I followed the instructions from the Java website:

```

sudo -s
mkdir -p /opt/google/chrome/plugins
cd /opt/google/chrome/plugins
ln -s /usr/local/java/jre1.7.0/lib/amd64/libnpjp2.so

```

I closed and reopened Chrome and then went back to the Java website to check it. No joy. 

I took a peek in my file manager. The plugin folder was created and libnpjp2.so is there, but properties for this file tell me it's a broken link. Did I do something wrong?

---

### Post by claracc on 2012-08-30
I have openjdk-7 and icedtea-7-plugin installed in my recently upgraded ubuntu 12.04. The icedtea plugin is shown in firefox 15 as IcedTea-web 1.2 (1.2-2ubuntu1.1) or iced-tea-web-plugin which is not recognized by firefox because it says unknown plugin.

When I go to a very simple applets page: [http://www.walter-fendt.de/ph14s/lever_s.htm](http://www.walter-fendt.de/ph14s/lever_s.htm) Icannot see the applet, there is a white space. So, for me there is a bug in icedtea-7 plugin in repositories since it cannot run java applets in web pages.

The only way to see applets now in 12.04 for me is to install oracle jave from webup8 repository: [http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html](http://www.webupd8.org/2012/01/install-oracle-java-jdk-7-in-ubuntu-via.html)

---

