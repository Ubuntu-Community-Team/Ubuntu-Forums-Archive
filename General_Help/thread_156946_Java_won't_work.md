---
title: "Java won't work"
date: 2006-04-08
forum: General Help
---

### Post by Jonas_Henricsson on 2006-04-08
I got a problem with Java on my mozilla browser. I've linked .mozilla/plugins to libjavaplugin_oji.so, and since then I get no error message about not finding java. But now the problem is that when I enter a site which uses Java, the browser stops working. I waited about 20 minutes and nothing happened. I had to kill the browser.

How can I solve this problem?

Thank you for your reply!

/Jonas

---

### Post by Perfect Storm on 2006-04-08
Which version of java do you use? And how did you installed it?

---

### Post by Jonas_Henricsson on 2006-04-08
I installed j2re1.4-mozilla-plugin with Synaptic Package Manager. Should I get another version?

/Jonas

---

### Post by Jonas_Henricsson on 2006-04-08
Does anyone have any ideas? I would really like to get this fixed, but I'm not sure where to start...

---

### Post by Sef on 2006-04-08
> I've linked .mozilla/plugins to libjavaplugin_oji.so

I would undo that and download the extension for it from getting started icon on the firefox browser.

---

### Post by nanotube on 2006-04-09
[QUOTE=Jonas_Henricsson]I got a problem with Java on my mozilla browser. I've linked .mozilla/plugins to libjavaplugin_oji.so, and since then I get no error message about not finding java. But now the problem is that when I enter a site which uses Java, the browser stops working. I waited about 20 minutes and nothing happened. I had to kill the browser.

How can I solve this problem?

Thank you for your reply!

/Jonas[/QUOTE]

it may be that whatever java applet you are trying to access requires some sun java features that are not present in the open source java implementation that comes with ubuntu.

to install the official sun java, go to the link in my sig, and find the "install sun java" section, and follow instructions. :)

---

### Post by Perfect Storm on 2006-04-09
Another option is: [HOW-TO: Building your own Java 1.5 package]("http://ubuntuforums.org/showthread.php?t=76735&highlight=java")
Before you use it you might enable universe and multiverse in your sourcelist. Also getting the basic compiling tools:
```
sudo apt-get install build-essential
```

---

### Post by adamkane on 2006-04-09
**Install Java SDK the hard way (FYI):**

Add the universe and multiverse repositories, if you haven't already:
 [http://easylinux.info/wiki/Ubuntu#Ho...a_repositories]("http://easylinux.info/wiki/Ubuntu#How_to_add_extra_repositories")
 
 Install fakeroot and java-package:
 
      ```

sudo apt-get install fakeroot java-package

```[LEFT]
[/LEFT]
         
 Download and install J2SE Development Kit 5.0 Update 6 (Linux Platform):
 [http://java.sun.com/j2se/1.5.0/download.jsp]("http://java.sun.com/j2se/1.5.0/download.jsp")
 
```

cd ~/Desktop
[LEFT] fakeroot make-jpkg jdk-1_5_0_06-linux-i586.bin
sudo dpkg -i sun-j2sdk1.5_1.5.0+update06_i386.deb
sudo update-alternatives --config java
[/LEFT]
  
```[LEFT]   
[/LEFT]
   
Select:
 /usr/lib/j2sdk1.5-sun/bin/java
 
More Ubuntu Java installation info:
 [https://wiki.ubuntu.com/RestrictedFormats#java]("https://wiki.ubuntu.com/RestrictedFormats#java")
  
** Install Java JRE or Java SDK the easy way:**

 You can install Java JRE or SDK with Automatix:
 [http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix  .29]("http://easylinux.info/wiki/Ubuntu#Installing_additional_software_.28Automatix.29")
 
 or by adding the Sevea repository:
 [http://www.ubuntulinux.nl/source-o-matic]("http://www.ubuntulinux.nl/source-o-matic")

```

sudo apt-get install sun-j2jre1.5

```

or

```

 sudo apt-get install sun-j2sdk1.5

```

---

### Post by nanotube on 2006-04-09
artificial intelligence, adamkane: 
all that is already listed in my ubuntu chronicles page - that's why i linked to it. ;)

---

### Post by trent dillman on 2006-04-09
I got your answer:

You linked the wrong plugin. There are multiple plugins, one in (on my system) ns7 and one in ns7-gcc29.

---

### Post by Jonas_Henricsson on 2006-04-09
No, I don't *think* I chose the wrong folder..

Anyway, I followed adamkane's instructions (the hard way :)) and now it works. Thanks alot, guys!

---

### Post by trent dillman on 2006-04-09
Sorry.

I had similar problems a while back on a friend's Mandriva box...

...@#!$ Runescape....


I'm glad you got it running!

---

