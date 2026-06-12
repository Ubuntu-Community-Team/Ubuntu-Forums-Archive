---
title: "Java runtime web app issues ubuntu 10.10"
date: 2010-12-16
forum: General Help
---

### Post by priesty on 2010-12-16
I'm having touble with a java web application.  It's online learning through SEEK's skillport website and it uses JRE runtime environment to display the content.  I have java installed for Ubuntu as per java.com's website instructions, and I can launch my web application, however it only displays the left half of the screen. The other half is just not there. 
I'm running Ubuntu 10.10, all updates applied.  I've also tried installing OpenJDK Runtime Environment (IcedTea6 1.9.2) but the same sypmtoms occur. 
Skillport's support centre only supports Suse Linux so they couldn't help me.  
I'm wondering if Java is the problem or maybe a browser issue? I've tried in Firefox as well as Google Chrome for linux - same result.
Currently I'm having to boot into Windows so I can do my study. Everything else works fine in Ubuntu.
Any suggestsions?

---

### Post by priesty on 2011-03-23
Ok so I finally found the answer to this issue. It has been bugging me for nearly 2yrs!!
The problem was too many installations of java installed at the same time. If you are experiencing the same issue as me (java not working properly) then remove all versions that you have installed and follow the instructions very carefully from the java website, the standalone installer steps.
At the end of the day all you are doing is downloading the file, extracting its contents to a folder you have root permissions to, and creating a shortcut or linked file to the '.so' file and putting it in the firefox plugins directory. 
It actually does make sense to only have one version of software installed at the one time - the same logic applies to flash player or ATI video drivers in Linux.

---

