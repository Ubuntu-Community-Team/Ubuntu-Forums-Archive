---
title: "Java crashes Firefox"
date: 2012-03-10
forum: General Help
---

### Post by jakslev on 2012-03-10
Firefox crashes whenever I enter the website: [https://ebanking.danskebank.dk/html/index.html?site=DBNBEN&secsystem=DI](https://ebanking.danskebank.dk/html/index.html?site=DBNBEN&secsystem=DI)

```
The problem is a JAVA applet running on the right hand side of the page. Java seems to work other places but when I run Firefox in terminal I get the following output:

(firefox:3216): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.2)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

(java:3255): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Mar 10, 2012 4:24:47 PM <WARN> DANID_DIGITAL_SIGNATUR appletdk.pbs.applet.bootstrap.new - Not using whitelisted class classloader: net.sourceforge.jnlp.runtime.JNLPClassLoader
Mar 10, 2012 4:24:47 PM <INFO> Thread-4 - init
Assertion failure: rt->onOwnerThread(), at /build/buildd/firefox-10.0.2+build1/build-tree/mozilla/js/src/jsapi.cpp:6316

(crashreporter:3312): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

Any suggestions? It seems to load fine in Chromium :s

Cheers, 

jakslev:popcorn:

---

### Post by 0011235813 on 2012-03-10
> **jakslev said:**
> Firefox crashes whenever I enter the website: [https://ebanking.danskebank.dk/html/index.html?site=DBNBEN&secsystem=DI](https://ebanking.danskebank.dk/html/index.html?site=DBNBEN&secsystem=DI)

```
The problem is a JAVA applet running on the right hand side of the page. Java seems to work other places but when I run Firefox in terminal I get the following output:

(firefox:3216): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
java version "1.6.0_23"
OpenJDK Runtime Environment (IcedTea6 1.11pre) (6b23~pre11-0ubuntu1.11.10.2)
OpenJDK 64-Bit Server VM (build 20.0-b11, mixed mode)

(java:3255): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
Mar 10, 2012 4:24:47 PM <WARN> DANID_DIGITAL_SIGNATUR appletdk.pbs.applet.bootstrap.new - Not using whitelisted class classloader: net.sourceforge.jnlp.runtime.JNLPClassLoader
Mar 10, 2012 4:24:47 PM <INFO> Thread-4 - init
Assertion failure: rt->onOwnerThread(), at /build/buildd/firefox-10.0.2+build1/build-tree/mozilla/js/src/jsapi.cpp:6316

(crashreporter:3312): Gtk-WARNING **: Unable to locate theme engine in module_path: "pixmap",
```

Any suggestions? It seems to load fine in Chromium :s

Cheers, 

jakslev:popcorn:
It's probably a coding issue within the site. I recommend you use Chromium or another browser to open the page. Alternatively, you could use NoScript to block the Java element. You have installed NoScript on Firefox, right?

PS: No decent programmer would use Java on a webpage anyway, what  exactly is the content you're trying to view?
PSS: Stay away from obscure plugins. Obscure plugin downloads are often used as scams, where the scammer embeds a highly unusual plugin, and tells the viewer to install the plugin by giving them a link to malicious website. The download usually just installs malware, or installs the plugin with malware! In worst case scenarios, you don't even have to download anything; you just get a Trojan through malicious JavaScript! Now, I'm not saying a Danish banking site would do that, just keep it mind, hence why I suggested NoScript add-on.

---

### Post by jakslev on 2012-03-10
Thanks for the attempt. 

The java plugin named "NEMID" is - unfortunately - the only solution in Denmark to sign and authenticate yourself towards banks (all of them) and the government :(

I am sure it's crappy - but still - there must be a work around - it used to work.. 

The NEMID applet thing is running on several other places, Danske Bank is the biggest bank in Denmark :)

If I do the NoScript plugin, I assume that I would block it right? :o)

Cheers, 

jakslev

---

### Post by 0011235813 on 2012-03-10
> **jakslev said:**
> Thanks for the attempt. 

The java plugin named "NEMID" is - unfortunately - the only solution in Denmark to sign and authenticate yourself towards banks (all of them) and the government :(

I am sure it's crappy - but still - there must be a work around - it used to work.. 

The NEMID applet thing is running on several other places, Danske Bank is the biggest bank in Denmark :)

If I do the NoScript plugin, I assume that I would block it right? :o)

Cheers, 

jakslev
I would use another browser, and test to see how it works in Firefox until a later date. 
As for NoScript, I assumed there was something wrong with the Java element within the site that was crashing the 'fox. If however, as you have said, you need the Java element for authentication purposes, then no, NoScript won't solve the problem. NoScript would only prevent the site from crashing your browser.

Sorry that I can't help you more; my firewall seems to be broken again!

---

### Post by Gremlinzzz on 2012-03-10
Did you try updated version of Oracle (Sun) Java :popcorn:
you can install by copy and paste 
[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

if you don't have folder opt, just go to file system where it should be and create folder name it opt then open right click anywhere inside and choose open terminal /then just follow the sites instructions 
once some one couldn't find or didn't have folder opt

---

### Post by jakslev on 2012-03-12
Didn't try that. Are you able to see the page I posted? And what does it say in terminal when you do? Maybe there is something that makes sense if we compare the outputs? 

As it works in Google Chromium - I suspect it could be a plugin that is wrong? I am using the IcedTea plugin for firefox version 1.1.3-1ubuntu1.1. 

I am not sure how it works on Chromium - if it also has a plugin?

Cheers, 

jakslev

---

### Post by lykeion on 2012-03-15
I tested browsing to the site and it crashed in Firefox 11, and worked in Chromium 17. Both are using the same IcedTea Java Plugin. But my experience is that Firefox crashes very often ever since they started to issue new versions frantically. Last stable one was Firefox 3.6. My suggestion would be to use Chromium for this.

---

### Post by Pjotr123 on 2012-03-15
> **Gremlinzzz said:**
> if you don't have folder opt (...) once some one couldn't find or didn't have folder opt

Everybody has the folder /opt in his system, because this important system folder is there by default. In every Linux distribution that I know of, which is quite a lot. :-)

/opt is part of the Filesystem Hierarchy Standard as outlined by the Linux Foundation:
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard)

If somebody would claim that he has no /opt in his system, I absolutely disbelieve that. Probably somebody who has few computer skills and is very inaccurate.... :-)

---

### Post by baekgaard on 2012-03-16
The current best solution seems to be this one:

 - Type about:config in the adressline
 - Say yes to being cautious
 - Type dom.ipc.plugins.java.enabled into the filterline
 - Change the value to true, by doubleclicking the line
 - Close the tab
 - Restart firefox

Read more e.g. here: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/927065](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/927065)

---

### Post by jakslev on 2012-03-16
> **baekgaard said:**
> The current best solution seems to be this one:

 - Type about:config in the adressline
 - Say yes to being cautious
 - Type dom.ipc.plugins.java.enabled into the filterline
 - Change the value to true, by doubleclicking the line
 - Close the tab
 - Restart firefox

Read more e.g. here: [https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/927065](https://bugs.launchpad.net/ubuntu/+source/firefox/+bug/927065)

Thanks a lot! That seemed to work!

---

### Post by 0011235813 on 2012-03-16
> **jakslev said:**
> Thanks a lot! That seemed to work!
I'm glad it worked for you then. Can you please mark this thread as solved?

---

### Post by madsbola on 2012-04-09
Thx, another Dane is saved by this amazin Ubuntu Forum

Best regards
Mads, Denmark

---

### Post by KFoder on 2012-04-14
And another Dane saved, thanks to the community =D>

Kim

---

### Post by HJessDK on 2012-04-25
- Type about:config in the adressline
  - Say yes to being cautious
  - Type dom.ipc.plugins.java.enabled into the filterline
  - Change the value to true, by doubleclicking the line
  - Close the tab
  - Restart firefox

---

