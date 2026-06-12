---
title: "script to mount smbfs shares, guidance plz"
date: 2006-03-15
forum: General Help
---

### Post by crxyem on 2006-03-15
ok say I'd like to add a line in /etc/network/interface , and create an executable script called mountsmbfs.sh , do you think something like this would work , and can someone help me with the syntax thanks 

overall requirements, after wlan0 is up, check status to ensure it's functional, also check what the SSID is so I don't try to mount shares when I'm on a differnet AP, then mount shares and exit

```

  # The loopback interface
        iface lo inet loopback

  # The first network card
         iface wlan0 inet dhcp
         pre-up wpa_supplicant -i wlan0 -D hostap -c /etc/wpa_supplicant.conf
         pre-up sleep 5
         post-up /<pathtoscript>/mountsmbfs.sh

```

```
    
#! /bin/bash

X="up"
Y="MyWAPname"

if [$X 	== wlan0 status &&  $Y == $SSID #not sure how to do this yet];then
     mount -t smbfs  //servername/sharename /mountdirectory >
              credentials=/home/myhomedirectory/.smbpasswd dmask=777 fmask=777

    else
        null
fi
exit

```

I'm looking to do something like this because when I set my laptops acpi management mode to standby/suspend when the lid is closed, upon opening the lid again the samba shares are lost, and I'd like them to remount when the nic comes back up.

If anyone else has a better idea that would be great

Thanks in Advance
D.

---

### Post by crxyem on 2006-03-16
bump ...

---

