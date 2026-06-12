---
title: "Update makes my WIFI stop working Dell 1018"
date: 2011-01-07
forum: General Help
---

### Post by Phantom3D on 2011-01-07
Hi,

I have installed the wifidrivers needed to use the wifi on the 1018 in Ubuntu Netbook Edition. It works until I get asked to install 5 (Sorry, don't remember their name) more updates, now I can not see Wireless networks  under the networkmanager, It does not help installing the driver again, and I can not remove it either. It says the driver is activated but not in use. Also note that in desktop mode I lost my other workspaces, I can not change what window is on top and the quit, minimize and full window on windows is not there anymore.

Yesterday I had the problem so I reinstalled ubuntu, and it worked again, but I did not know what triggered it untill now..

I am pretty new to ubuntu so I don't know where to start..

Thanks

---

### Post by Phantom3D on 2011-01-07
I think it might be the Linux Kernel Image for version 2.6.3.5, That one is the biggest of the updates. But I do not dare to try again, I don't have time for another re-installation of ubuntu.

Is it usualy this "scary" to update your system? Never had any problems with my old eee pc900..

---

### Post by markovuc on 2011-03-02
It is possible that kernel update caused this problem.

If that is the case, try to boot to 'older' kernel (when computer starts, and you get grub screen to choose what to boot).

If kernel upgrade messed things up, this should help. You will start the system with older kernel, which I guess had everything configured/installed correctly to have wifi working.

---

