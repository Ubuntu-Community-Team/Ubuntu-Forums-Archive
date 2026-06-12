---
title: "How to install Java plugin into Firefox?"
date: 2010-03-09
forum: General Help
---

### Post by GreenRaccoon on 2010-03-09
I'm new to Linux and I'm trying to get my Java plugin to work in Firefox.  I already installed Java (I think).  I dual boot Ubuntu 9.10 64 bit with Windows Vista.

I have to install Java on my Ubuntu in order to log into my network, so I downloaded the Java package in Vista and put it on a flash drive.  I typed *sudo su* into Terminal, entered my password, then used *cd* to change my directory.  Then I typed in *sh jre-6u18-linux-x64.bin* and the license agreement came up.  I kept going down and accepted the agreement.  A new file appeared on my desktop.  I checked my Firefox plugin list and Java was not in it.  I restarted my computer to see if that would work, but it didn't.

What do I do next to install the plugin into Firefox?

Thanks guys!

---

### Post by sandyd on 2010-03-09
```

sudo apt-get install -y sun-java6-bin sun-java6-plugin
```
use tab to accept EULA

---

### Post by wojox on 2010-03-09
This is a good thread for installing the latest Java for 32 or 64 bit: [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by GreenRaccoon on 2010-03-09
That site was awesome wojox.  Thanks!  Best tutorial I've seen for linux yet.  [http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by DarkHellBird on 2010-03-20
Another happy Camper "http://sites.google.com/site/easylinuxtipsproject/java#TOC-Install-JRE-32-bit-", that site really did the job for me, thanks to all.

---

