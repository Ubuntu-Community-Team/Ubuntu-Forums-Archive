---
title: "Adobe flashplayer - ubuntu 9.10"
date: 2009-10-21
forum: General Help
---

### Post by MichaelDance on 2009-10-21
Error: Dependency is not satisfiable: libnspr4-dev

Description:
Adobe Flash Player plugin version 10
This package will download the Flash Player from Adobe. It is a Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use the Flash plugin. This package officially supports the following browsers:
Firefox 2.x, Firefox 3.x, SeaMonkey 1.11 

From
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29)

Do you know the problem or is it a bug like WineHQ wont install on 9.10 for me, and other programs.

---

### Post by MelDJ on 2009-10-21
tried the flashplugin-nonfree package in synaptic?

---

### Post by MichaelDance on 2009-10-21
> **MelDJ said:**
> tried the flashplugin-nonfree package in synaptic?

I have tried the Synaptic

---

### Post by jose158 on 2009-10-30
I'm having the same problem, when I go to install adobe-flashplugin from Synaptic, it gives me an error that reads: ```
adobe-flashplugin:
 Depends: libnspr4-dev  but it is not installable


```
This is a clean install of Ubuntu 9.10 with nothing else installed.

---

### Post by celem on 2009-10-30
No good for 64-bit system.

> **MichaelDance said:**
> Error: Dependency is not satisfiable: libnspr4-dev

Description:
Adobe Flash Player plugin version 10
This package will download the Flash Player from Adobe. It is a Netscape/Mozilla type plugin. Any browser based on Netscape or Mozilla can use the Flash plugin. This package officially supports the following browsers:
Firefox 2.x, Firefox 3.x, SeaMonkey 1.11 

From
[http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29](http://get.adobe.com/flashplayer/thankyou/?installer=Flash_Player_10_for_Linux_%28.deb%29)

Do you know the problem or is it a bug like WineHQ wont install on 9.10 for me, and other programs.

---

### Post by Hunter362 on 2009-10-30
> **celem said:**
> No good for 64-bit system.

Installed via Ubuntu Software Center with no errors.

---

### Post by PMix on 2009-11-02
Same thing happened for me. Make sure all the latest updates are installed. That took care of things for me.

---

