---
title: "How to use hughesnet status meter"
date: 2010-10-18
forum: General Help
---

### Post by w1ll1am on 2010-10-18
Hello if anyone here used hughesnet they know that it sucks haveing a download limit and having a tool to tell you how much download you have left would be nice. Well there is an adobe AIR application for this and here is how to install it on Ubuntu or Ubuntu64bit.

Download and install the ia32-libs package by opening your System -> Administration &#8211; > Synaptic Package Manager

Now download adobeAIR [http://get.adobe.com/air/](http://get.adobe.com/air/) 

make it executable by right clicking on it and going to permissions and clicking the "Allow executing file as program" 

now install it

cd /home/YourUserName/Downloads

sudo ./AdobeAIRInstaller.bin 

Now you go to hughesnet website and click on install [http://services.hughesnet.com/service_tools/Status_Meter/](http://services.hughesnet.com/service_tools/Status_Meter/)

after is is installed you will have a status meter on your top tool bar and a desktop icon.

---

### Post by ricaltman on 2011-04-26
Not so solved. I'm using Ubuntu 10.10, installed Air from Adobe site, installed Hughesnet Status meter fro Hughes site, all looked well, but when I click on the Hughes Status meter icon, the lower right hand alert say "A Hughesnet Modem could not be found." I've changed the default [www.systemcontrolcenter.com](www.systemcontrolcenter.com) to 192.168.0.1 but still the same results. Also added 192.168.0.1 [www.systemcontrolcenter.com](www.systemcontrolcenter.com) to /etc/hosts and still same result.

---

### Post by ricaltman on 2011-05-02
> **ricaltman said:**
> Not so solved. I'm using Ubuntu 10.10, installed Air from Adobe site, installed Hughesnet Status meter fro Hughes site, all looked well, but when I click on the Hughes Status meter icon, the lower right hand alert say "A Hughesnet Modem could not be found." I've changed the default [www.systemcontrolcenter.com]("http://www.systemcontrolcenter.com") to 192.168.0.1 but still the same results. Also added 192.168.0.1 [www.systemcontrolcenter.com]("http://www.systemcontrolcenter.com") to /etc/hosts and still same result.I'm running Ubuntu 11.04 and have found a way to get a FAP monitor working. I had to install KDE to do it. The FAP monitor is "FAP Status" by Dustin Widmann written as a "Plasmoid," which will only run in a KDE desktop environment.

What I did:
1. Installed Ubuntu 11.04.
2. Installed "KDE-standard" from Synaptic Package Manager.
3. Installed 3 additional packages from Synaptic Package Manager.
    a. python-kde4 (4:4.6.2b-0ubuntu1.1)

    b. python-kde4-dev (4:4.6.2b-0ubuntu1.1)

    c. plasma-scriptengine-python (4:4.6.2a-0ubuntu5)

4. From the KDE desktop, clicked icon in the upper right corner "Panel Tool Box, then "Add Widgets" then "Get New Widgets" then "Download New Plasma Widgets" then type "Hughesnet" in the search bar. "FAP Status" by Dustin Widmann should appear, click on install. It will then show up in the "Add Widgets" toolbar in your "Panel Tool Box." Just doubleclick it and it should appear in your panel at the bottom (or top) of your desktop.

---

