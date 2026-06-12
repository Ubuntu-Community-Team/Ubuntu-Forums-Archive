---
title: "Wireless Problem"
date: 2009-07-23
forum: General Help
---

### Post by AxelMan0 on 2009-07-23
I'm using Ubuntu 9.04 and my wireless card (Intel 4965 AGN) randomly stopped working after a restart today. The last thing I did to change anything was type "hciconfig hci0 inqmode 0" into the rc.local file. I have since deleted that line of code and that was for bluetooth so I don't see how that could have messed up my wireless anyway. If I boot from the Ubuntu LiveDVD then the wireless works fine. I've looked all over the internet and there doesn't seem to be any working solution, so I was just wondering where Ubuntu keeps all of its wireless-related files. Since wireless works from the LiveDVD I figured I could just copy all those folders over to a thumb drive and replace the ones on my hard drive.

---

### Post by AxelMan0 on 2009-07-23
I fixed it! All I had to do was sudo gedit /etc/NetworkManager/nm-system-settings.conf and change [ifupdown] managed=false to [ifupdown] managed=true

now why couldn't I find this thread before.... xD [http://ubuntuforums.org/showthread.php?t=1109585](http://ubuntuforums.org/showthread.php?t=1109585)

---

