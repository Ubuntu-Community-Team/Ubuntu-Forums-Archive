---
title: "Trouble updating Java and perhaps other programs"
date: 2011-01-09
forum: General Help
---

### Post by life_pudding on 2011-01-09
Problem 1: Am having problem with a Java program.  Checked my version from oracles site and it is 6.20 .  Program works with 6.22 on another machine with different screen resolution.  Java was originally installed either with the initial installation or with Ubuntu Software center. Tried uninstalling and reinstalling with Ubuntu Software Center and did not help.  Tried installing from directions from Oracle site and did not help.  Now I have a directory with Java 6.23, and a directory with Java 6.22 .  When I look for Java with Synaptic Package Manager it shows a 6.22 version.  When I check what Java version is being used in browser on oracle's site it says I am using 6.20

Ideally I would like to be running 6.23 get updates when I do my update manager.

Possibly related problem 2: I have not had any Chromium or Firefox updates for like 3 weeks or perhaps never.  (did install around Thanksgiving.) using chromium 8.0.552.224 (68599) and Firefox 3.6.13 and on my other machine I get updates frequently.  Chromium was install with the Ubuntu Package Manager

Hardware: Thinkpad T60

Thanks.



Added Later:

I just did a   "which java" and it was pointing to an icedtea java.  So I removed the programs associated with icedtea and the which java then pointed to the oracle version 22.  Then I opened Firefox and it said I needed a plugin, icedtea, and I added it and I am back to where I was.

---

### Post by lykeion on 2011-01-10
OpenJDK Java and IcedTea browser plugin is installed by default in Ubuntu. For Lucid and later this is v6.20b. OpenJDK/IcedTea is the open source implementation of the Java by Sun (now Oracle). For most of the time this should work fine when browsing pages with Java.

However if you go to java.com it will tell you to update to Oracle Java. This is no mystery since java.com is owned by Oracle. But if you don't have any problem with Java on web pages I'd suggest you to disregard Oracle's advice and leave it as it is.

If you really need to replace IcedTea with Sun (Oracle) Java browser plugin you should install the **sun-java6-plugin** package. Lucid and later have v6.22 of Oracle's Java. You have to enable the Partner repository first (but you seem to already have done that since you see version 6.22 of Java in Synaptic).

You should know that in Ubuntu you use a package manager (Synaptic/Ubuntu Software Center) to update and install programs. Downloading and installing stuff from the web manually is a Windows habit, and you should only do it if you know what you're doing.

---

