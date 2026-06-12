---
title: "Ubuntu 11.10 help please."
date: 2012-04-29
forum: General Help
---

### Post by Camilia on 2012-04-29
I installed ubuntu 11.10 with a CD. Everything worked fine. Upgrades got installed automatically and then utube videos not viewable. So I reinstalled 11.10. Set upgrades to not upgrade automatically. Today got notice that have partial upgrades.  Get notice to post sudo in terminal. Try to view video on comcast.net. Get notice that I need to upgrade the latest flash drive. I clicked on it and opened it with archive manager. Restarted firefox. Still get notice to upgrade flash drive. I can't find the terminal. Also can't find the synapse manager. 

Oh where, oh where is the the terminal and synapse manager? 

Why are upgrades making it impossible to view videos on utube and comcast?

---

### Post by 3rdalbum on 2012-04-29
> **Camilia said:**
> I installed ubuntu 11.10 with a CD. Everything worked fine. Upgrades got installed automatically and then utube videos not viewable. So I reinstalled 11.10.

Ubuntu has never shipped with the Flash Player plugin, so it has never been able to view Youtube videos out-of-the-box.

You simply have to install the flashplugin-nonfree package, and then restart your browser, and you'll be able to play your videos.

To answer your other question, Synaptic Package Manager has not come with Ubuntu for a year now. Ubuntu Software Center replaces it in the default install, but you can still use Software Center or Apt-get to install Synaptic. Or click the Ubuntu logo and type "synaptic" and it will appear as the first result - when you click it, Software Center will open and allow you to install Synaptic.

The Terminal is available from the Dash (click the Ubuntu icon, type Terminal and it will pop up as the first result). Or press Control-Alt-T at any time to bring up a terminal.

Finally, now that you're on 11.10 you should change your profile on Ubuntu Forums to reflect that.

---

### Post by Camilia on 2012-04-30
> **3rdalbum said:**
> 
You simply have to install the flashplugin-nonfree package, and then restart your browser, and you'll be able to play your videos.

Did that and still not able to view videos. There was another plugin to install. While the flashplugin was installing I walked away.When I came back the option to download the other plugin was gone. Where do I find the missing plugins?

Downloaded the synapse manager. From there downloaded Flashplugin-nonfree and IcedTea6 -plugin.

Then downloaded flash player from adobe site. 

Still not able to view videos on utube

Tried to upgrade to 12.10. Afterwards just got blue screen with desktop icons. Thus reinstalled 11.10 Now have no problems viewing videos.

---

