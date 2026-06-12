---
title: "Opening blocked JNLP file"
date: 2011-04-28
forum: General Help
---

### Post by emaloley on 2011-04-28
Hello! I'm very new to Linux. I am trying to open a JNLP file but I get the error message:

"The file is not marked as executable.  If this was downloaded or copied from an untrusted source, it may be dangerous to run.  For more details, read about the executable bit."

This file is from a trusted source. Any ideas? Thanks!!

---

### Post by RJ12 on 2011-04-28
You need to right click on the file and go to properties, then on the permissions tab there should be a check box that says "Allow executing of this file as a program" or something like that, check the box and close the properties window. You should now be able to run your program :)

---

### Post by emaloley on 2011-04-28
Ok..I'm not getting the error message anymore. But when I double-click the file I get four options; 1. Run in Terminal (which won't do me any good) 2. Display (which does nothing) 3. Cancel 4. Run (which also does nothing)

Any further suggestions?? Thanks for your help!!

---

### Post by RJ12 on 2011-04-28
Hmm... a jnlp file looks like a JavaWebStart file... do you have Java (I think you need the Oracle one and not the OpenJDK one) installed?

---

### Post by emaloley on 2011-04-29
No I do not have Java installed from Oracle :(

I tried installing it a few weeks ago, but I don't have a clue how to install things on Linux and I created more problems. I tried following the read me on Oracle's website for installing it but it still goes over my head.

Here are my 6 download options for Java 6 JRE which includes JavaWebStart to open my application:

**[SIZE=1] Java SE Runtime Environment 6 Update 25[/SIZE]**

**[SIZE=1]Download[/SIZE]**

[SIZE=1] Linux x86 - RPM Installer[/SIZE][SIZE=1]20.06 MB  [/SIZE][SIZE=1] [IMG]http://www.oracle.com/ocom/groups/public/@otn/documents/digitalasset/115899.gif[/IMG] jre-6u25-linux-i586-rpm.bin[/SIZE][SIZE=1] 
Linux x86 - Self Extracting Installer[/SIZE][SIZE=1]20.58 MB  [/SIZE][SIZE=1] [IMG]http://www.oracle.com/ocom/groups/public/@otn/documents/digitalasset/115899.gif[/IMG] jre-6u25-linux-i586.bin[/SIZE][SIZE=1] 
Linux Intel Itanium - RPM Installer[/SIZE][SIZE=1]20.06 MB  [/SIZE][SIZE=1] [IMG]http://www.oracle.com/ocom/groups/public/@otn/documents/digitalasset/115899.gif[/IMG] jre-6u25-linux-ia64-rpm.bin[/SIZE][SIZE=1] 
Linux Intel Itanium - Self Extracting Installer[/SIZE][SIZE=1]20.58 MB  [/SIZE][SIZE=1] [IMG]http://www.oracle.com/ocom/groups/public/@otn/documents/digitalasset/115899.gif[/IMG] jre-6u25-linux-ia64.bin[/SIZE][SIZE=1] 
Linux x64 - RPM Installer[/SIZE][SIZE=1]19.62 MB  [/SIZE][SIZE=1] [IMG]http://www.oracle.com/ocom/groups/public/@otn/documents/digitalasset/115899.gif[/IMG] jre-6u25-linux-x64-rpm.bin[/SIZE][SIZE=1] 
Linux x64 - Self Extracting Installer[/SIZE][SIZE=1]20.20 MB  [/SIZE][SIZE=1] [IMG]http://www.oracle.com/ocom/groups/public/@otn/documents/digitalasset/115899.gif[/IMG] jre-6u25-linux-x64.bin[/SIZE]

So I'm sure I don't want either "Linux Intel Itanium" download, but I don't know if I need to go for a Linux x64 download or x86. What's the difference? Beyond that, what is the difference between a RPM Installer and a Self Extracting Installer?

Thanks for your patience and help..

---

