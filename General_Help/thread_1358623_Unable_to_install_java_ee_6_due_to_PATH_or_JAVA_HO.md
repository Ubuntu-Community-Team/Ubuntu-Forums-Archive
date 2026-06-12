---
title: "Unable to install java ee 6 due to PATH or JAVA_HOME"
date: 2009-12-18
forum: General Help
---

### Post by cincibcat on 2009-12-18
I installed java 6 through synaptic.  After downloading the java ee 6 sdk from sun's website, when I try and run the file i get the following message:

```
Could not locate a suitable jar utility.
Please ensure that you have Java 6 or newer installed on your system
and accessible in your PATH or by setting JAVA_HOME

```

I followed the post which describes how to set the path in .bashrc:
[http://ubuntuforums.org/showpost.php?p=2138426&postcount=7](http://ubuntuforums.org/showpost.php?p=2138426&postcount=7)

After restarting my computer I still receive that message.

Any ideas on a fix or another approach on installing Java EE 6?

---

### Post by MadCatmkII on 2009-12-28
Might [this]("http://ubuntuforums.org/showthread.php?t=1113039") help you?

---

### Post by rivera151 on 2010-01-18
I'm getting the same error.  No matter what I do it cannot find the jar utility to proceed with the installation script.  Any other ideas?

---

### Post by standingcat on 2010-04-25
I had the same issue when trying to install java ee 6 with only the jre environment installed. I solved it by installing the java 6 sdk and then installing java ee 6.

---

### Post by azetaguionbajo on 2010-08-19
> **standingcat said:**
> I had the same issue when trying to install java ee 6 with only the jre environment installed. I solved it by installing the java 6 sdk and then installing java ee 6.

THANKS A LOT!;) That works and the java 6 sdk package Is ready to download @ the software center of ubuntu.

---

