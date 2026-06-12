---
title: "Firefox 3.6.3 + Java"
date: 2010-04-15
forum: General Help
---

### Post by patman0623 on 2010-04-15
My Java plugin is not loading on Firefox. Help! I need it to load, but FF doesn't even recognize Java is installed. It works on Google Chrome (which would be nice... except the plugin is buggy there)

Here's the background
* I'm running Firefox 3.6.3, through the repository on 
```
http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu
```. 
* My process list includes: 
```
23679 ?        00:00:00 firefox
23688 ?        00:07:31 firefox-bin
```
* I run NoScript, but I've had it work before w/NoScript, and everything is currently allowed. I'm fairly sure it has rather to do with FF 3.6.3.
* My about.config settings:
```
java.default_java_location_others;/usr/java
java.default_java_location_solaris;/usr/j2se
java.global_java_version_file;/etc/.java/versions
java.java_plugin_library_name;javaplugin_oji
```
* My directory settings:
```
patrick@patrick-laptop:/usr/lib/jvm$ ls
java-6-sun  java-6-sun-1.6.0.15
```

---

### Post by lovinglinux on 2010-04-16
See [http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by Irony on 2010-04-16
> **lovinglinux said:**
> See [http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")
Thanks for that!

I tried the repository version first but that didn't work, fortunately your link worked for me running 64 bit Karmic with the latest 64 bit firefox from the ppa.

---

### Post by patman0623 on 2010-04-18
> **lovinglinux said:**
> See [http://sites.google.com/site/easylinuxtipsproject/java]("http://sites.google.com/site/easylinuxtipsproject/java")I would follow those instructions if I even could. But the site says to create a plugins directory; that's not possible there's already a *file* named plugins in the ~/.mozilla directory.

---

### Post by lovinglinux on 2010-04-18
> **patman0623 said:**
> I would follow those instructions if I even could. But the site says to create a plugins directory; that's not possible there's already a *file* named plugins in the ~/.mozilla directory.

So put the plugin inside it.

---

### Post by patman0623 on 2010-04-18
> **lovinglinux said:**
> So put the plugin inside it.*File*, not directory. There is a *file* called plugins.

---

### Post by lovinglinux on 2010-04-18
> **patman0623 said:**
> *File*, not directory. There is a *file* called plugins.

Can you read it? I would check what it is, but deleting it probably won't cause any problems. Just delete it and create a folder.

---

### Post by patman0623 on 2010-04-18
> **lovinglinux said:**
> Can you read it? I would check what it is, but deleting it probably won't cause any problems. Just delete it and create a folder.Well it's 9MB big, and I'd sure hate to see my plugins disappear. And I can't read it: gedit says something about not recognizing the character encoding (I miss the old days of being able to view raw code). I am definitely making a backup, and I'm going to try that.

---

### Post by lovinglinux on 2010-04-18
> **patman0623 said:**
> Well it's 9MB big, and I'd sure hate to see my plugins disappear. And I can't read it: gedit says something about not recognizing the character encoding (I miss the old days of being able to view raw code). I am definitely making a backup, and I'm going to try that.

Your plugins won't disappear, but I would make a backup of it, just in case some application added it. Nevertheless, I never saw such file there.

---

### Post by patman0623 on 2010-04-18
Worked, thank you.

---

### Post by mountmike on 2010-04-22
Thanks so much for pointing me here: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

I tried many other solutions first to no avail.

I followed the section entitled:
**[B][SIZE=3][COLOR=#000000][SIZE=4][B]HOW-TO  FOR 32 BIT UBUNTU**[/SIZE][/COLOR][/SIZE][/B][/B]

and that finally did it for me!

---

