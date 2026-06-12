---
title: "Wireless PPPOE problems"
date: 2011-03-11
forum: General Help
---

### Post by LakatosI on 2011-03-11
The dorm that I am living provides us with free internet through our university. To connect to the Internet you have to use Dial-Up combined with a plain connection to the network (What I'm saying is that in order to dial-up you first have to connect normally to the local area network through cable wireless.) This works fine in Windows, but in Ubuntu in the network connections sections I can only dial-up through cable, being there no equivalent for wireless. 

Recently they started to upgrade our network, and a consequence of this is that there are no working cable connections left in our dorm. Our room was the only fortunate one to survive this disaster (our room for some reason is connected differently than the other rooms), and in order for all of us to use the Internet we plugged in our cable into a wireless router. My problem now is that I can't connect to the Internet through Ubuntu.

I did find a temporary solution. First I connect normally to the wireless network (it is password protected), thus gaining access to the University network, and then I can run pppoeconf in the terminal to dial-up and gain access to the Internet. My problem now is that the next time I booted my network connections icon has disappeared from the Notifications Area, and I can't connect to the wireless network to dial-up. Did pppoeconf overwrite some important settings?
Is there any solution to my problem?

---

### Post by grahammechanical on 2011-03-11
To get the Network icon back in the panel, right click the panel and select Add to Panel. From the list select Notification Area and click Add.

You should also make sure the the Network Manager is one of your startup applications. Go to System>Preferences>Startup Applications and look for Network Manager. Make sure it has a tick mark set against it. You may need to reboot.

Have you tried using Network manager to set up the dial-up part of your connection? I think it under Edit connections>DSL.

Regards.

---

### Post by LakatosI on 2011-03-11
The Network Connections icon disapeared from the Notifications Area. You can readd it as many times as you want, it won't reaper. 
Also, setting DSL only works for cabled connections. I have to achieve this through wireless.

---

### Post by LakatosI on 2011-03-12
Shameless self-bump. 

No suggestions?

---

### Post by marshag63 on 2011-03-12
I've never heard of this kind of setup before - that is weird.  I don't know what to tell you about the networking icon disappearing - annoying.  

My suggestion is to setup the network manager to automatically connect to the wireless network.  From that point, use a script for the ppoe part - you can probably set it up so that it checks that the wireless connection is present and then proceeds with the ppoe connection.  

You can use a terminal command to verify your network connection if you find no solution to the disappearing network icon.  In a terminal type "sudo iwlist scan" and enter your password.  This will show all available connections, interface used, essid, etc.

What things do you have to do when you use windows to connect - outline the steps and maybe someone will have a suggestion.

MDG

---

### Post by dineshs on 2011-03-14
> My problem now is that the next time I booted my network connections icon has disappeared from the Notifications Area, and I can't connect to the wireless network to dial-upTry step-1 and 2 [here]("http://ubuntuforums.org/showpost.php?p=9611450&postcount=2").Your icon will be back.Now connect wireless as usual and just run pon command.(You need not run pppoeconf)

---

