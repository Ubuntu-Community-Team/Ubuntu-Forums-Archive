---
title: "lossy wifi connection"
date: 2012-09-22
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2012-09-22
my [laptop]("http://reviews.cnet.com/laptops/hp-compaq-cq60-215dx/1707-3121_7-33496182.html") get a 40% signal 
my [old desktop]("http://ubuntuforums.org/showpost.php?p=12250587&postcount=44") gets a 55-65% signal
laptop works flawlessly over wifi at the same location while desktop gets 16% loss (ping test [100 count] )
the desktop has a "Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller" with a huge linksys logo on the PCI card
it has these 3 packages installed for wifi
[FONT=Courier New]b43-fwcutter[/FONT], [FONT=Courier New]firmware-b43legacy-installer[/FONT],  and [FONT=Courier New]firmware-b43-installer[/FONT]
i am measuring the signal with a script i made```
#!/bin/bash
if [ -z "$1" ]; then
    W="wlan0"
else
    W=$1
fi
W=`iwlist $W scan | grep Quality | sed 's/=/\n/' | tail -1 | sed 's/ /\n/' | head -1`
W=`gcalctool -s "$W*100"`
W=`echo $W | sed 's/\./\n/' | head -1`
echo $W%
exit
```

---

### Post by Bucky Ball on 2012-09-22
Do you require the legacy installer? If not, remove and restart. Just a punt but there might be some conflict there. How close to the router are you?

---

### Post by pqwoerituytrueiwoq on 2012-09-22
well within my routers range, i even upped my routes wifi voltage (usually keep it under volted to keep it from being the diameter of a football field)
router is a wtr54gl
laptop will still work just fine at that location with my router at 15mW (42mW it default)

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx#Installing_b43_drivers)
i tried the legacy one 1st as this said to, i had also tried it without the legacy only seems to work with both :?

---

### Post by pqwoerituytrueiwoq on 2012-09-24
even my [original NDS](http://t3.gstatic.com/images?q=tbn:ANd9GcTLZJtwXLGiYBH_BxtGJ7ZieRToHy0qrmIgMqGEpTBtPwzL8PWLAQ) works at farther from the router than this old box and that is with the wireless under-volted to 15mW
the desktop does not even wan to work when the router is at 55mw
is there something wrong with my antenna design?

---

