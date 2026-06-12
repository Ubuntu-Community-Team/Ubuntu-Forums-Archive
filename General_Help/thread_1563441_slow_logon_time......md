---
title: "slow logon time....."
date: 2010-08-29
forum: General Help
---

### Post by prasanthdotm on 2010-08-29
hai... i hav a mac in which i did a triple boot... everything ws fine until today when all of sudden the boot time became high, m unable to access network... upto logon screen everything s fine... when i logon, first i get the wallpaper... 5 seconds in, i get the desktop shortcuts... and after 20 seconds, i get the panels... still no network access... if i select network setting or somthin lyk that from the systems tab, i get the window with all tabs lyke vpn, wireless, mobile broadband etc... but it s sutck there... i can just watch it ... dats all... plz help.... i hav class tomorrow and i need to get the system ready by then,...:confused:


well i just boot to lucid and tried playin with the startup apps...
the problem seems tobe my network manager..... anyway to reinstall it??? plzz reply....

---

### Post by varunendra on 2010-08-29
As a quick remedy, you may try to uninstall Network Manager from  synaptic and install wicd instead. However, I've heard that interface of  wicd is not as good as NM with wireless, so in that case you may need  to go through lengthy troubleshooting process :(.

I am assuming that for now, you are more concerned about Wireless  connectivity rather than slow booting time. If it is not so, please post  what exactly do you want to solve immediatly.

If you suspect a broken system, you may try booting in '**Recovery Mode**' (press and hold 'Shift' key while booting) and try '**dpkg**' there.

If you want to give NM a shot, please post the outputs of (none of these  needed if your problem is other than network connectivity):
```
ifconfig -a
iwconfig
sudo dhclient
route -n
cat /etc/network/interfaces
cat /etc/NetworkManager/nm-system-settings.conf
dig www.google.com
dmesg | tail
```

---

