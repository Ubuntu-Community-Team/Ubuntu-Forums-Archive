---
title: "UBuntu and Wireless"
date: 2006-03-09
forum: General Help
---

### Post by Nixforce on 2006-03-09
I would like to convert from WinXP to Ubuntu , but need to make sure our wireless network will work.. The modem is a adsl barracuda modem with wireless LAN .. Will the adsl wireless work on Ubuntu, and if so, is there a guide to get it running, as never run ubuntu on a network before.. Any guidelines would be great..

---

### Post by george_apan on 2006-03-09
It doesn't matter what modem you have. What matters is the wireless card you have in your PC. Some of them work out of the box, some need their windows drivers to get them working and a few don't work at all. If you're lucky you're not in the last category.

---

### Post by Nixforce on 2006-03-09
Once im home tonight, i will get the modem details and search online for drivers and post here , maybe someone has used one! Thanks

---

### Post by Nixforce on 2006-03-09
I think it is a Barracuda adsl modem with wireless lan, but will confirm when home tonight

---

### Post by dpaint4 on 2006-03-09
I had the same question, so I booted the LiveCD, and entered my WEP Key and Network info into the 'Networking' dialog in the 'Administration' menu. Worked like a charm. For me, Ubuntu has been the first truly easy wireless Linux.

Try the LiveCD and see for yourself what the setup will be like.

---

### Post by TrendyDark on 2006-03-09
Most likely you can use ndiswrapper for your wireless driver setup. If you're using the LiveCD, I'm not sure if you can implement this solution, but with an installed version you can easily. Search wiki.ubuntu.com for "ndiswrapper".

---

### Post by dpaint4 on 2006-03-09
[QUOTE=TrendyDark]Most likely you can use ndiswrapper for your wireless driver setup. If you're using the LiveCD, I'm not sure if you can implement this solution, but with an installed version you can easily. Search wiki.ubuntu.com for "ndiswrapper".[/QUOTE]

Well, hopefully that won't be neccessary for him. I don't know the hardware, but to my thinking that'd be his last-ditch effort if the thing isn't natively supported, which is the only thing he could test with the LiveCD anyway, right?

One note about my experience, being very new to the OS and very happy with it, the Wireless setup in the LiveCD was actually a smidge harder than in the installed version, in that (and this is no big deal) I had to figure out where to go to type in my network info.

When installing, one of the first things it askef for was my Network ID and WEP Key. So by the time the desktop loaded, I was already online. It was magical.

---

### Post by Nixforce on 2006-03-09
If i try the Live CD version and the wireless works, does that mean the install version would be fine?

---

### Post by Nixforce on 2006-03-09
Ive got version 5.04 , and waiting for the newer version, if i install with this, is the update easy?

---

### Post by Rinzwind on 2006-03-09
Yes. On both questions.

---

### Post by Peter41az on 2006-03-09
In my laptop, (an Averatec 3700 running Ubuntu Breezy ) i have a ralink 2500 that works out of the box on ubuntu... on the desktops, all 7 are running DLink Airplus G cards and Ubuntu that also worked right out of the box. USB cards are a joke, havent found one that worked right yet. To add a note here, the Dlinks show up as ath0, the ralink on the Averatec laptop shows up as ra0. wep works fine, and since i own a computer company, im in probably 6 different offices a day, no problems scanning and switching wireless to wireless. the card i know does NOT work is a Linksys wusb54g USB speedbooster card.

---

### Post by Peter41az on 2006-03-09
Sorry for another post, but i had a hunch. i tried the usb wireless wusb54g that wasnt version 2, and ill be damned if it didnt pop right up as wlan0. so its just the version 2 with speedbooster that wont work :)

So i was wrong, and i shall go eat my crow now :)

---

