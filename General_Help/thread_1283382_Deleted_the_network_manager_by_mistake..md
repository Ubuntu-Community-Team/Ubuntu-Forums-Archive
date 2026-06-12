---
title: "Deleted the network manager by mistake."
date: 2009-10-05
forum: General Help
---

### Post by kostaz8 on 2009-10-05
I deleted by mistake the network manager and now i cant connect to the internet with my netbook to install it i downloaded a deb file to install it offline but it gives me an error about some dependencies.I installed them but now the libnm-glib-vpn0 is failing.What i do wrong is any other way to install the network manager?Thx

---

### Post by undecim on 2009-10-05
connect via ethernet and run 
```
sudo dhclient
```if that connects properly, you can use
```
sudo aptitude install network-manager
```

EDIT: Actually, you might not even need to connect if the packages are still cached on your computer. Just try the second command from above and see if it works

---

### Post by nothingspecial on 2009-10-05
If you have no ethernet, only wireless then

```
sudo ifconfig wlan0 up
```
```

sudo iwconfig wlan0 essid [COLOR="Red"]*yournetworkname*[/COLOR]
```
```

sudo iwconfig wlan0 key [COLOR="Red"]*yourwirelesskey*[/COLOR]
```

Followed by the above commands.

This just get`s your wireless connected from the terminal.

---

### Post by kostaz8 on 2009-10-05
Problem solve guys thnx!

---

### Post by kostaz8 on 2009-10-05
But know i cant make it permanent if im on ethernet i have to type sudo dhclient to connect and when i connect wireless its says that i am connected but no internet at all i installed the network manager without problems.

---

### Post by Iowan on 2009-10-05
I'm not using the remix, but on "regular" Ubuntu, System>Preferences>Startup Applications has a checkbox for Network Manager.

---

### Post by kostaz8 on 2009-10-06
I did this but nothing.

---

### Post by Iowan on 2009-10-06
Perhaps a permutation of [this]("http://ubuntuforums.org/showpost.php?p=8063853&postcount=5") post?

---

