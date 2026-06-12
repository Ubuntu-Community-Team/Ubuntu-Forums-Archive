---
title: "Entering WEP Key into BreezyBadger"
date: 2006-04-04
forum: General Help
---

### Post by ComputersXP on 2006-04-04
Hey 

how do i enter a WEP key into Ubuntu BreezyBadger ....

a wep key is a network password u have to enter to connect to ur network 

Thanks John

---

### Post by karthik085 on 2006-04-04
Networking (System->Administration) might help.

[QUOTE=ComputersXP]Hey 

how do i enter a WEP key into Ubuntu BreezyBadger ....

a wep key is a network password u have to enter to connect to ur network 

Thanks John[/QUOTE]

---

### Post by ronmarley1 on 2006-04-04
Wifi-radar is another option you may want to look at.  It's in the repos.

---

### Post by ComputersXP on 2006-04-05
Dont u need to have net access to install the addons !!!

---

### Post by karthik085 on 2006-04-05
If you need net access and wireless is not working, try other ways: ethernet, modem, ...
Or copy the necessary files from a computer that has net access and transfer it to a floppy, cd, usb drive....and copy to your ubuntu system

---

### Post by ComputersXP on 2006-04-05
i have the network found but all i need to do is enter a WEP key 

and were can i find 
Wifi-radar

---

### Post by ComputersXP on 2006-04-05
im gonna try kubuntu because i dont like thr gnone desktop 

i like KDE more

---

### Post by RikoW on 2006-04-05
If you go the the menu Systen -> Administration -> Networking (as mentioned before) you should get a list with the available network cards on your system.

Choose on the wireless card and click the Properties button. There you can set ESSID and Wep key.

No need to install anything in addition.

Cheers,

            Riko

---

### Post by ComputersXP on 2006-04-05
nope nothing there all i get is IP Gateway

---

### Post by AndyCooll on 2006-04-05
Modify your network interfaces file.

```
sudo gedit /etc/network/interfaces
```

Where your wlan details are, add your ESSID if it's not already there and your WEP key. I'm at work at the moment so cannot tell you the exact format, maybe someone else on these forums can supply that information.

:cool:

---

### Post by RikoW on 2006-04-05
This is how it looks in me /etc/network/interfaces file:

```
iface eth1 inet dhcp
wireless-essid My-ESSID
wireless-key My-Wep-key
```

(of course, My-XXX replaced with your settings)

I don't understand why you don't see it in the networking dialog, though. do you use a native linux driver for the wlan card or the ndiswrapper/linuxant driver approach? Does that have anything to do with it?
I used to run the linuxant wrapper for the windows driver on my old, old Suse installation before Ubuntu came along. They use a special config programm to set ESSID and Wep-Key.

For ndiswrapper, you find instructions here:

[URL="http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Configure_interface:"]http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation#Configure_interface:

[/URL]

Cheers,

             Riko

---

### Post by ComputersXP on 2006-04-05
i have the linux drivers that ubuntu installs

ill try wat people have said as i now have reinstalled unbutu ..didnt like the KDE enviroments in kubuntu

---

