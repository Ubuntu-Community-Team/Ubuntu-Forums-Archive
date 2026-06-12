---
title: "Jre installation on ubuntu 10.04"
date: 2012-02-29
forum: General Help
---

### Post by sagar_322 on 2012-02-29
Hi all, I want to install sun-java6-jre in ubuntu 10.04 I added the  repository "deb [http://archive.canonical.com/](http://archive.canonical.com/) lucid partner" and when  I  do sudo apt-get install  sun-java6-jre I get error saying package not  found for sun-java6-jre and so on. Any help would be appreciated. Thanks  in advance

---

### Post by Tiganjero on 2012-02-29
Try executing: ```
sudo apt-get purge openjdk*
cd ~/
sudo wget https://raw.github.com/flexiondotorg/oab-java6/master/oab-java6.sh -O oab-java6.sh
sudo chmod +x oab-java6.sh
sudo ./oab-java6.sh
sudo apt-get install sun-java6-jre
sudo apt-get install sun-java6-plugin
```
Worked for me..

Cheers,
George

---

### Post by QIII on 2012-02-29
That is an unsafe method and I would suggest that you NOT do that.  You would be depending on a process and script by a third party about whom you know little or nothing.  There are other sites offering scripted installation - but, again, you don't see or control the process.  Do you know who "flexiondotorg" is?  Flexion.org is some individual's home page.  Do you trust him?  He may be a stand up guy as far as we know.  But do you want to gamble?  Are you able to interpret oab-java6.sh if you open it in a text editor?

The Java in the repos is old and contains security flaws.  Java will never be updated in the repos because Oracle has withdrawn licensing for such.  So don't do that either.  The package hasn't been in that partner repo for some time.

Please use the method at 

[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

If you want to install Java 7, that will also work, provided that you modify the commands appropriately.

In the tutorial above, you are using the "official" installation file you download directly from java.com without third party intervention and with commands that are explained so that the process is transparent and clear.

I don't like where they direct the symbolic link to the plugin, but it will work just fine.  Unfortunately, if you have multiple users you have to repeat a few commands for the plugin.

---

### Post by sagar_322 on 2012-03-02
Thanks that helped me.. :). But why I am unable to install java by apt-get install. Did Oracle rally removed sun java stuff from ubuntu repo.?

---

