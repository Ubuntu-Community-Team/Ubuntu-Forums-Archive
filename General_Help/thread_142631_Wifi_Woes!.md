---
title: "Wifi Woes!"
date: 2006-03-10
forum: General Help
---

### Post by newbdude on 2006-03-10
I have an airlink 101 AWLC3025 wireless Cardbus adapter. Ndiswrapper says invalid drivers, and through the wifi control panel as soon an i enable it, it just switches back to disabled.

I HAVE NO HARD LAN LINE!!!! :(

any help is appericiated!!!!

---

### Post by ltmon on 2006-03-10
There is a good article on setting up ndiswrapper here:[https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto](https://wiki.ubuntu.com/WifiDocs/Driver/Ndiswrapper?action=show&redirect=SetupNdiswrapperHowto).

It includes instructions for if you don't have another connection.

I looked up your model on the ndiswrapper wiki ( [http://ndiswrapper.sourceforge.net/mediawiki/index.php/](http://ndiswrapper.sourceforge.net/mediawiki/index.php/), and search for AWLC3025).  It claims that it should work perfectly using ndiswrapper >= 1.08 and the default drivers from the WinXP cd for your card.

See if either of those resources can help you out.

Cheers,

L.

---

### Post by newbdude on 2006-03-11
Ok I figured out whats wrong. The WEP key wasn't being stored from Kcontrol (never using that again!!!). I also found out that I had the version of ndiswrapper from ADept, so it doesn't have all of the -utils, including modprobe, so I need to install the newest one. Any help is still appericiated!

---

