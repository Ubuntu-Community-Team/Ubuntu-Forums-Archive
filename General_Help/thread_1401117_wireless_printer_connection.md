---
title: "wireless printer connection"
date: 2010-02-07
forum: General Help
---

### Post by kevgrn114 on 2010-02-07
Hi, new here and to Ubuntu.  So far everything has been easier and better than windows! WOW!!!  
I am having trouble getting connected to my wireless print server. Normally in windows i choose network printer and enter //kjg-nas/lp and it finds it ok. I've tried all the options in Ubuntu a few different ways but still cant get it to connect.

My printer is an HP9800 connected to a buffulo NAS server.

Any suggestions?

Thanks,
Kevin

---

### Post by omaralqady on 2010-02-07
Try hplip: [http://hplipopensource.com/hplip-web/index.html]("http://hplipopensource.com/hplip-web/index.html")

It worked for me.

---

### Post by TriadHonor on 2010-02-07
Yeah, I also use **HPLIP**, and it works fine, but with some printers ( **all-in-one series** ) you need a scanner addon.
So first install **HPLIP** from Synaptic then, if your scanner don't work, install **XSANE** and **HPJIS**.

Finally remind to install the **GUI** to manage your printer simply, the packet is **HPLIP-GUI**.

Start it and add your printer choosing if it work with cable or wireless, some version need a temporary USB connection also for wireless, but not all.

When the installation finish if the small HP logo don't show in the top bar, **reboot** and **relog**.

**Done** :popcorn:

---

