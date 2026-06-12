---
title: "Problems installing xmms-status-plugin"
date: 2010-02-25
forum: General Help
---

### Post by donfisico on 2010-02-25
Hi, I have Ubuntu 9.04 (64 bits) and  I have recently installed xmms, there was a little problem doing it so but I manage to do it anyway. The problem  was that when I tried 
sudo apt-get install xmms, ( I modified the source.list previously of course including
deb [http://www.pvv.ntnu.no/~knuta/xmms/jaunty/](http://www.pvv.ntnu.no/~knuta/xmms/jaunty/).) the system answered me "Impossible to get [http://www.pvv.ntnu.no/~knuta/xmms/jaunty/./xmms_1.2.11-1_amd64.deb](http://www.pvv.ntnu.no/~knuta/xmms/jaunty/./xmms_1.2.11-1_amd64.deb)  The size differs". At such answer I did not what to do but to download myself (wget) the package and then install it with dpkg -i.I wonder If anybody had have the same problem because I searched everywhere without results. Anyway, I did the trick fine and I was able to install and run xmms. The problem is now when I tried to install xmms-statutus-plugin. I have also downloaded and tried to install with dpkg -i, but the system claimed that it needs libglib1.2. Ok, I said to  myself, and I installed libglib1.2-dev via apt-get install. Nevertheless trying now to install again that plugin, system says "package libglib1.2" when it is pretty clear that these library is now installed. What I can do???

---

