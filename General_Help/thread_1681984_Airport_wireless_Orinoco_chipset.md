---
title: "Airport wireless Orinoco chipset"
date: 2011-02-05
forum: General Help
---

### Post by spiky001 on 2011-02-05
I have install 10.04 on a Ibook G3 I,m having problems with the wireless. Network manager detects wireless networks but wont connect. Lspci dosn't show airport card lsmod shows Orinoco as used by airport, In iwconfig wireless shows up as eth1, any ideas on getting it to work plz

---

### Post by spiky001 on 2011-02-05
I have found a workaround I followed this thread [http://ubuntuforums.org/showpost.php?p=9289758&postcount=57](http://ubuntuforums.org/showpost.php?p=9289758&postcount=57) 
```
sudo mv /lib/firmware/agere_sta_fw.bin /lib/firmware/agere_sta_fw.bin.bak ; sudo pccardctl eject ; sudo pccardctl insert
```

As reported in thread it did take some reboots, If you edit the wireless connection with correct details it will auto log on to network on reboot, when shutdown or reboot from using connection it losses connection info, If you log out 1st then shutdown it will reconnect. I Would like any info on making connection stick with just shutting down plz.

---

