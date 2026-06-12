---
title: "broken packgate after update ubuntu 10.04"
date: 2011-04-07
forum: General Help
---

### Post by tmy on 2011-04-07
After doing a update in ubuntu 10.04 this is the message I get: E: /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~lucid1_i386.deb: trying to overwrite '/usr/share/hal/fdi/information/20thirdparty/31-apple-mobile-device.fdi', which is also in package libimobiledevice0 0

How can I recover from this ? The problem is made worse because I can not install any software because of a broken package on the system use broken filter to locate it 

I don't have any clue what to do can someone help me out and be gentle I have very little knowledge of command line thank you

---

### Post by falko on 2011-04-07
Do you use the stock /etc/apt/sources.list, or did you modify it?

---

### Post by plucky on 2011-04-07
> **tmy said:**
> After doing a update in ubuntu 10.04 this is the message I get: E: /var/cache/apt/archives/libimobiledevice1_1.0.6-1ubuntu1~lucid1_i386.deb: trying to overwrite '/usr/share/hal/fdi/information/20thirdparty/31-apple-mobile-device.fdi', which is also in package libimobiledevice0 0

How can I recover from this ? The problem is made worse because I can not install any software because of a broken package on the system use broken filter to locate it 

I don't have any clue what to do can someone help me out and be gentle I have very little knowledge of command line thank you

Open Synaptic Package Manager ( System > Administration > Synaptic Package Manager) and navigate to **Custom Filters > Broken** and attempt to fix it there.

Post back any problems.


Good Luck

---

### Post by tmy on 2011-04-07
> **falko said:**
> Do you use the stock /etc/apt/sources.list, or did you modify it?

Thank you for taking time to help me, I have added :

[http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu](http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu) Lucid main


[http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) Lucid main

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) Lucid partner


[http://ppa.launchpad.net/pmcenery'ppa/ubuntu](http://ppa.launchpad.net/pmcenery'ppa/ubuntu) Lucid main

Hope that is enough information the strange thing is that I have never had a problem before and only added **[http://ppa.launchpad.net/pmcenery'ppa/ubuntu](http://ppa.launchpad.net/pmcenery'ppa/ubuntu) Lucid main** AFTER the problem started in a attempt to fix it.

Thank you again for your help look forward to your further assistance.

---

### Post by tmy on 2011-04-07
> **plucky said:**
> Open Synaptic Package Manager ( System > Administration > Synaptic Package Manager) and navigate to **Custom Filters > Broken** and attempt to fix it there.

Post back any problems.


Good Luck

Thank you thank you thank you that worked great but I had to do it twice and just did not know what or how to fix a broken package, really pleased as it is so annoying to have a problem as it also stops other programs being installed.

Why would it have problems in the first place ? Thank you so much hope this helps out others.                         :P


tmy

---

### Post by tmy on 2011-04-07
> **tmy said:**
> Thank you for taking time to help me, I have added :

[http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu](http://ppa.launchpad.net/elementaryart/elementarydesktop/ubuntu) Lucid main


[http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu](http://ppa.launchpad.net/clipgrab-team/ppa/ubuntu) Lucid main

[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) Lucid partner


[http://ppa.launchpad.net/pmcenery'ppa/ubuntu]("http://ppa.launchpad.net/pmcenery%27ppa/ubuntu") Lucid main

Hope that is enough information the strange thing is that I have never had a problem before and only added **[http://ppa.launchpad.net/pmcenery'ppa/ubuntu]("http://ppa.launchpad.net/pmcenery%27ppa/ubuntu") Lucid main** AFTER the problem started in a attempt to fix it.



Thank you again for your help look forward to your further assistance.

Thank you for your help I managed to fix it by using the broken packet in synaptic thank you again

tmy          :P

---

### Post by plucky on 2011-04-07
> [http://ppa.launchpad.net/pmcenery'ppa/ubuntu](http://ppa.launchpad.net/pmcenery'ppa/ubuntu) Lucid main

That line has a ' instead of a / is the reason why it doesn't connect as I am getting a 404 error.

Your problem is a broken package libimobiledevice1_1.0.6-1ubuntu1~lucid1_i386.deb

Try synaptic package manager to fix the problem

Good Luck

---

