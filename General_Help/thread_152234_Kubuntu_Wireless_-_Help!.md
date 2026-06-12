---
title: "Kubuntu Wireless - Help!"
date: 2006-03-29
forum: General Help
---

### Post by Hangetsu on 2006-03-29
I posted this in the beginner section, and after further thought I probably should have posted it here first:

OK, I managed to trash my Ubuntu installation - Not surprising, but I'm learning alot as I trash my machine 

I'm going to put in a new install using Kubuntu -- I like the KDE interface better than GNOME personally. However, I'd like to get some information regarding Kubuntu before I try again.

I have a WPA2 - protected wireless network (AES), and I have a NetGear WG311v3 card installed. With Ubuntu, setting this up is a breeze with ndiswrapper, ndisgtk (gui for ndiswrapper), and wpa_supplicant.

Are these all available for Kubuntu? When I tried Kubuntu last night, it didn't seem to have ndiswrapper available for use. Also, is there an equivalent to ndisgtk for KDE (or is ndisgtk independent of windows environment)?  I know these are available from sourceforge, but I have zero experience running make on files and would prefer to use the deb files from (K)ubuntu.

From what I've read doing a search on these boards, wpa_supplicant should install the same way as with straight Ubuntu - Is this the case?

Thanks again for the help everyone. The community support for this distro is absolute fantastic, I just hope I learn enough someday to return the favor to future newbies moving from Microsoft!!

---

### Post by Hangetsu on 2006-03-31
OK, I have the system working - woohoo!  In case someone else runs into a problem, I thought I'd share what I found:

First, do NOT try to use the gui tools to activate your wireless card.  They are crap in KDE.  You will need to modify /etc/network/interfaces on your own.

Second, if you use WPA2 authentication, remember to check if your AP broadcasts.  I have mine turned off for security, so ep_scan = 2 and scan_ssid=1 in your wpa_supplicant.conf file.  Nothing more fun than banging your head against the wall trying the passphrase several times, rebooting, and seeing the failed on time synchronization during bootup :D

In any event, after a day or so, its working.  And I know alot more about wireless networking in Linux than I did before, so I consider it a rewarding learning experience!!

---

### Post by alchemyuk on 2006-04-29
Can you please talk me through all the things you did to get this wifi card working? thanks

---

### Post by bobbymcsteels on 2006-04-29
i had just setup my wireless card lastnite and workin fine all i did was download my windows driver from my cards website and this:-
```
sudo apt-get install ndiswrapper-utils
sudo ndiswrapper -i /home/whereyoudownloadedthedriver/mycardsdriver.ini
sudo ndiswrapper -m 
```
Then
```
sudo ndiswrapper -m
```
to check that its listed
then cos I use dhcp i did:-
```
dhclient wlan0
```

that should work.... cool lil app to keep tabs on it is kwifimanager
```
sudo apt get install kwifimanager
```

hope this works for you

---

