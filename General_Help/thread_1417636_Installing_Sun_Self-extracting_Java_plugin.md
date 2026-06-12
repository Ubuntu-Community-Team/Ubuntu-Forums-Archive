---
title: "Installing Sun Self-extracting Java plugin"
date: 2010-02-27
forum: General Help
---

### Post by Kerubu on 2010-02-27
Hi,

I use ubuntu 8.10 with the ubuntu packaged version of firefox, however i would like to use the latest java runtime environment from the Sun website and NOT use the ubuntu packages.

the problem I have is that i do not know where to place the link to my latest java plugin file.

Where is the location for mozilla plugins ? the directory ~/.mozilla/plugins didn't exist and even when I created one and put a link there I still had the older version of Java.

anyone help or point me to a place detailing where this can be done ? I have done it before but forgotten and I need my memory jogging.

thanks
Kerubu

---

### Post by mick222 on 2010-02-27
Try this [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
Easy to follow instructions here.

---

### Post by Kerubu on 2010-02-27
> **mick222 said:**
> Try this [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)
Easy to follow instructions here.

Thanks for that mick, however that gives a system wide installation of Java which i'm hoping to avoid.

I'd like to just tell Firefox which java version to use. I've done this in the past but I can't remember how. i just need to put a ling to the java library in a 'plugins' directory but there are several directories to choose from and so far putting a link in them hasn't worked. (I remember having this problem before, I just can't remember which directory I ended up using !)

Anyone else any ideas ?

---

### Post by flyingsliverfin on 2010-02-27
i did this a little while ago... so lets see... i did it all through the terminal, it was easier.

first u donwload it. then execute the .bin. then u have a folder. make a folder in /usr called java (this is what id did btw). move the folder created by the .bin to the /usr/java. find the name of your firefox folder in /usr/lib/firefox____ (the exact filename. for me it was firefox-3.0.8 ). cd into the firefox folder then into the plugins folder. do the      ln -s /usr/java/jre1.6.0_18 (this it the newest version) /plugin/i386/ns7/libjavaplugin_oji.so

that should do it

---

### Post by Kerubu on 2010-02-27
> **flyingsliverfin said:**
> i did this a little while ago... so lets see... i did it all through the terminal, it was easier.

first u donwload it. then execute the .bin. then u have a folder. make a folder in /usr called java (this is what id did btw). move the folder created by the .bin to the /usr/java. find the name of your firefox folder in /usr/lib/firefox____ (the exact filename. for me it was firefox-3.0.8 ). cd into the firefox folder then into the plugins folder. do the      ln -s /usr/java/jre1.6.0_18 (this it the newest version) /plugin/i386/ns7/libjavaplugin_oji.so

that should do it

Hi flyingsilverfin,

Tried that, still doesn't work. I seem to have umpteen plugin directories under various parent directories e.g. mozilla,firefox,firefox-3.0.17 etc etc. I've tried changing the links in all of these but it still sees the old version of Java.

I use the Ubuntu install of firefox and I can't seem to find out information on which directory holds the plugins..

ARRRGGHHH !!! ](*,)

---

### Post by flyingsliverfin on 2010-02-28
use the one in firefox-3.0.17 under /usr/lib. cd into the firefox directory, then the plugins one. 

u probably already tried that...

maybe its more basic: are u going it as root or using sudo? u need to to be able to edit /usr directories...

---

### Post by Kerubu on 2010-03-01
> **flyingsliverfin said:**
> use the one in firefox-3.0.17 under /usr/lib. cd into the firefox directory, then the plugins one. 

u probably already tried that...

maybe its more basic: are u going it as root or using sudo? u need to to be able to edit /usr directories...

I found a temporary solution.

It appears I have a link called 'java-6-sun' under /usr/lib/jvm which points to version 14 of the jre. changing this link to version 18 makes the latest java version plugin work in firefox, however it breaks java and javac from the command line.

I suspect this link is due to the Ubuntu install of java and firefox. I think I'm going to go back to version 14 of the jvm anyway as using version 18 did not fix the crashes i was having in Facebook and java

---

### Post by flyingsliverfin on 2010-03-01
k

---

