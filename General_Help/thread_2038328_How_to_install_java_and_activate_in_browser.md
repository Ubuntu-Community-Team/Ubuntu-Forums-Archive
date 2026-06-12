---
title: "How to install java and activate in browser"
date: 2012-08-06
forum: General Help
---

### Post by MichaelEber on 2012-08-06
I need to install java and get it activated in my browser.
When I go to the java site, it only offers RPM(?) format which acts like zipped files...just opening to show a bunch of folders.  No install process.

There does not seem to be a deb file available.  So how do I do this?

---

### Post by GeneralCody on 2012-08-06
You can do this:

put the line

```
deb http://www.duinsoft.nl/pkg debs all
```

in the file /etc/apt/sources.list, 

either using Software Sources from your System Menu or by editing the file in an editor (as root)or:
put this line in a file named (e.g.) duinsoft.list in the 
directory 

```
/etc/apt/sources.list.d
```

import the gpg key with the command (all on one line)

```
sudo apt-key adv --keyserver keys.gnupg.net --recv-keys 5CB26B26
```
enter the commands (two lines)
```

sudo apt-get update
sudo apt-get install update-sun-jre

```

or use Synaptic to install the package
installation of the Runtime Environment will follow automatically

---

### Post by jim_deadlock on 2012-08-06
The method for manually installing the latest version from java.com can be found here: [Click]("https://sites.google.com/site/easylinuxtipsproject/java")

---

### Post by ajgreeny on 2012-08-06
Have you tried the openjdk versions of java and the icedtea plugins?

They used to be a bit of a problem on some websites and with some java applications, but seem to work everywhere now, as far as I can see.

---

### Post by MichaelEber on 2012-08-06
I Installed OpenJDK but Chrome doesn't know that java is installed.

So how do I tell my browser I have java???

---

### Post by ajgreeny on 2012-08-07
When you go to a site that needs java using Chrome or chromium, a display notification will appear at the top of the page asking if you wish to enable the java plugin.  I can't remember if it is site specific or just a "first use" question.

You can go to [http://www.java.com/en/download/installed.jsp?detect=jre&try=1](http://www.java.com/en/download/installed.jsp?detect=jre&try=1) to test your java plugin, and you may then see the on screen dialog notification about enabling java that I spoke of.

---

### Post by 1976MrEMan on 2012-08-12
Hi, I'm a new ubuntu user, new to linux entirely as a matter of fact, using 12.04 on a 64-bit system. I have tried every tutorial I can find and followed instructions down to the letter. STILL no java runtime environment, just a mess of useless files! NONE of the tutorials work for me, and some seem to be skipping steps. Can anybody tell me a clear and concise way to install the oracle java environment (i don't need development) and possibly clean up this mess?

---

### Post by jockyburns on 2012-08-12
I installed the Open JDK version , together with the IcedTea plugins. When I navigate to a site that uses Java, I usually get a notification that the plugin is not up to date and get the option to install the latest plugin or  run this time. Selecting the install the latest plugin, just takes me to the Java download site (absolutely no help),** but**, selecting the "run this time" option does enable Java and everything works as it should. 
I think this is a known bug with Java and Linux OS's

---

### Post by cottfcfan on 2012-08-12
Try using the webupd8 java ppa. Works for me, & its simple:
```
sudo apt-add-repository ppa:webupd8team/java
```
```
sudo apt-get update && sudo apt-get install oracle-java7-installer
```

---

