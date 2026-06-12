---
title: "problem installing sun java"
date: 2010-05-13
forum: General Help
---

### Post by cmongini on 2010-05-13
i have problems installing sun java from internbet documentation it seems that the command would be: sudo apt-get install sun-java6-jre
but when i do it this is the answer that i get: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package sun-java6-jre is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package sun-java6-jre has no installation candidate

i tried also to install the debian package followin the instructions of the website, but a passwort is asked which is not the one that i gave in and that works for the sudo installations. so i &#7743; blocked there too 

can you help me? thanks i would appreciate it!

---

### Post by wojox on 2010-05-13
I like this how to [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU)

---

### Post by Smart Viking on 2010-05-13
Yes me too, i have Karmic.

What i ended up doing was searching for "sun java" in the package manager and install everything. I did have java then, but i could not use it in the net bank since the version was too old. (Or it gave me some server error saying something about the directory does not exist, and i figured that is because they only have the directory for the newest version of java)

There should be an easy way, that is one of the things that aren't for human beings. I still don't have the latest java version installed. :).

---

### Post by cbecker78 on 2010-05-13
open synaptic and search for "jre".  you can install it from there.  If you don't see the sun-java6-jre, you probably need to add the multiverse to your repositories.

---

### Post by Sef on 2010-05-13
Are you still using Breezy Badger, 5,10?  If so, the repositories have long been closed.  You might be able to install it from the java site, but I am not sure what dependency problems there will be, if any.  Your best option is to update to Lucid Lynx.

---

### Post by cmongini on 2010-05-13
no i alrteady installed version 10 but not updatet my profile ( had some years of ubuntu pause!)

---

### Post by howefield on 2010-05-13
> **cmongini said:**
> i have problems installing sun java from internbet documentation it seems that the command would be: sudo apt-get install sun-java6-jre

Enable the partner repository, reload the package list and all will be well.

System > Administration > Software Sources > Other Software tab.

Your terminal command will then work..

---

### Post by cmongini on 2010-05-13
the problem that i have concern the installation in Lucid Lynx.

---

### Post by Linuxforall on 2010-05-13
> **cmongini said:**
> the problem that i have concern the installation in Lucid Lynx.

Lucid has partner repo for sun java which needs to be enabled, it also enables auto update of Sun Java.

---

### Post by cmongini on 2010-05-13
thanks what are trhe repositories for the partner that i need (sorry i&#7743; new)

---

### Post by howefield on 2010-05-13
> **cmongini said:**
> the problem that i have concern the installation in Lucid Lynx.

I too have Lucid Lynx, you'll still find sun-java6-jre in the partner repository.

---

### Post by howefield on 2010-05-13
> **cmongini said:**
> thanks what are trhe repositories for the partner that i need (sorry i&#7743; new)

Go to System > Administration menu and load Software Sources.

Type in your password if prompted and press enter.

In the "Other Software tab", place a check in the box beside the partner repository. Then press close, then reload on the dialogue window that pops up.

Then back to you terminal command.

sudo apt-get install sun-java6-jre

---

### Post by Smart Viking on 2010-05-13
> **wojox said:**
> I like this how to [http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU](http://sites.google.com/site/easylinuxtipsproject/java#TOC-HOW-TO-FOR-32-BIT-UBUNTU)

Thank you, that worked! :D I did see similar guides when i googled it, but that was for older versions of java, thanks. :)

---

### Post by doas777 on 2010-05-13
also, after you install java, you may need to update your alternatives to work with it:

```
sudo update-java-alternatives -s java-6-sun
```

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

---

### Post by cap10Ibraim on 2010-05-13
> **cmongini said:**
> thanks what are trhe repositories for the partner that i need (sorry i&#7743; new)

join date : Jan 2006 :popcorn:

---

### Post by Smart Viking on 2010-05-13
> **cap10Ibraim said:**
> join date : Jan 2006 :popcorn:

Well, my mother have been using Different Linux distros over a time of more than 10 years, but she ain't much of a computer scientist i can assure you. :P

---

### Post by madmax75 on 2010-05-13
I did an upgrade from Karmic to Lucid, the Sun Java seems to have been replaced by the IcedTea version. 

Now, with certain applets this just hogs up all the CPU cycles and starts to heaten up my processors badly. I know this is a bug, but I would like to use the Java version instead. IcedTea just isn't an option in it's current state.

The problem is, I cannot locate the Sun Java version from the repositories. It is not there. And I don't have a "Partner repository" entry in my Software sources window.

I know there is the extremely crappy terminal-based installation option available from the Java website, but it has never worked for me. It is just horrible (even the documentation seems to be patchy). I mean, why can't they just provide a simple .deb package? They have .rpm for sure, but no .deb.

So I'm kind of stuck here. I will not waste my time with the terminal crap (It just does not work, period), I can't install from the repositories, because there are no "Partner" repositories (maybe this is because of the upgrade instead of clean install?). The open source versions just don't work, either.

So, what to do?

---

### Post by cmongini on 2010-05-13
to explicate about the new. i used ubuntu for 3 weeks in 2006 and then got back a couple of weeks ago.

---

### Post by cmongini on 2010-05-13
about repositories: in the meanwhile i found this:deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) to be added in  System > Administration menu and load Software Sources.( i haven tried it. otherwise install it manually as it is described here. [http://sites.google.com/site/easylin...-32-BIT-UBUNTU](http://sites.google.com/site/easylin...-32-BIT-UBUNTU) it worked for me too!

---

### Post by Cavsfan on 2010-05-13
This site has the best instructions I have found and I have used them several times with great success.

_[Easy Java Update Instructions]("http://sites.google.com/site/easylinuxtipsproject/java")_

If you have a 32 bit machine, instructions will be on the left, if 64 bit the instructions will be on the right.

---

### Post by howefield on 2010-05-13
> **madmax75 said:**
> The problem is, I cannot locate the Sun Java version from the repositories. It is not there. And I don't have a "Partner repository" entry in my Software sources window.

Try opening a terminal and use the command

```
sudo add-apt-repository “deb http://archive.canonical.com/ lucid partner”
```

---

### Post by Cavsfan on 2010-05-13
Here is a Java version tester site that will ensure you have successfully installed the most current version. 
BTW that site is tailored to install the latest version

_[Java Version Test]("http://www.javatester.org/version.html")_

---

### Post by Cavsfan on 2010-05-13
Sorry for butting in, but I have never been able to update Java except with the instructions from the site I posted on page 2 of this thread.
Let me know if they do not solve the problem.

I would bookmark it for future use. The site says to update it for the newest version, but each time I have needed 
it, it was already updated. I just had to follow the instructions.

---

### Post by 2hot6ft2 on 2010-05-13
If you're still having problems with java you may want to look here:
[http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40](http://ultimateeditionoz.com/forum/viewtopic.php?f=73&t=1080&start=40)
:popcorn:

---

### Post by cmongini on 2010-05-13
thanks for all the instructions i solved the problem with the instructions on [http://sites.google.com/site/easylin...-32-BIT-UBUNTU](http://sites.google.com/site/easylin...-32-BIT-UBUNTU) that i higly recommend and i got the application that i needed working

---

### Post by Cavsfan on 2010-05-13
> **cmongini said:**
> thanks for all the instructions i solved the problem with the instructions on [http://sites.google.com/site/easylin...-32-BIT-UBUNTU](http://sites.google.com/site/easylin...-32-BIT-UBUNTU) that i higly recommend and i got the application that i needed working

That site returns this:
**Not Found**

 **Error 404**

---

### Post by wojox on 2010-05-13
> **Cavsfan said:**
> That site returns this:
**Not Found**

 **Error 404**

Try this link [http://ubuntuforums.org/showpost.php?p=9292794&postcount=2](http://ubuntuforums.org/showpost.php?p=9292794&postcount=2)

---

### Post by Cavsfan on 2010-05-13
> **wojox said:**
> Try this link [http://ubuntuforums.org/showpost.php?p=9292794&postcount=2](http://ubuntuforums.org/showpost.php?p=9292794&postcount=2)


It's ironic that it's the same site I posted just scrolled down a bit,  but oh well...

---

### Post by howefield on 2010-05-13
> **Cavsfan said:**
> It's ironic that it's the same site I posted just scrolled down a bit,  but oh well...

Redundancy is alive and well, wojox posted it 4 hours before you did. ;)

---

### Post by Cavsfan on 2010-05-13
LOL I know! We are all just trying to help! Sometimes I even repeat myself...
Cheers!

---

