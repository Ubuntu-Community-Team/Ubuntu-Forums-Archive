---
title: "How do I 'Add ath_hal to the DISABLED_MODULES= '"
date: 2009-12-18
forum: General Help
---

### Post by dirtylcd on 2009-12-18
Hi,

Totally new to fiddling with linux. I have used terminal before. Installed UNR on my dads Acer Aspire One. Need to get wifi working. The guide suggests two methods, 
**ath5k Method**


and

madwifi.

For the first it says signal may be weak or drop out so i'll use the second. But it tells me to..

In order to have the wireless work after reboot, add the following line to /etc/modules ("sudo gedit /etc/modules") to automatically load the module when booting: 
ath_pciYou should now have working wireless. However you may want to do the following to prevent problems (the symbol mismatch) when the module is loaded: 
Add **ath_hal** to the **DISABLED_MODULES=** stanza in **/etc/default/linux-restricted-modules-common** 
(i.e. 'DISABLED_MODULES="ath_hal"')  


How do I add that line it refers to? And how do I add the latter phrase? This is really abstract. I don't know what I would be adding it TO let alone how to add it.

Thanks!

---

### Post by mikewhatever on 2009-12-18
Well, the guide is talking about the file /etc/default/linux-restricted-modules-common, and adding the line to it, namely <DISABLED_MODULES="ath_hal">. You can do that manually by opening the file for editing with <gksudo gedit /etc/default/linux-restricted-modules-common> and adding the required line. As a side note, Karmic doesn't have the linux-restricted-modules package, and so might not have the above file.

---

