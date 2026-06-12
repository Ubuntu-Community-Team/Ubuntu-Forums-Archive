---
title: "No internet connection to bt home hub 2"
date: 2011-05-29
forum: General Help
---

### Post by coneill659 on 2011-05-29
I have downloaded ubuntu 11.04 and the internet does not connect to by bt home hub 2. 

The computer connects to bt Fon and bt openzone but not to the home hub. It recognises that the home hub is there and accepts the password but then tries to connect and fails.

I tried running the trouble shooting help section for wirless on ubuntu and it advised me to go on to a forum as the computer was not fully recognising my network adapter.

My wireless connector is intel RJ45.

Thanks :)

---

### Post by iclestu on 2011-05-29
Hey there.

Can you access your network from another system or device? If so I can offer the following suggestion...

I have a home hub. It sometimes doesnt like it if you have it set up for persistant ip but the computername changes....  You could try powering down the ubuntu machine, accessign the router settings from your other system (just point a webbrowser at [http://192.168.1.254/](http://192.168.1.254/)), going to advanced settings, home network, then the icon for your ubuntu machine and just delete it. Then reboot the ubuntu machine. I occasionally have this issue and this seems to resolve it. (I dont know what I am doing enough to proffer a reason tho ;) )

As an alternative, if you have no reason to use anything other than the default router settings just hit the rest to factory settings button (you might need a paperclip or pin or something)

---

### Post by dandnsmith on 2011-05-29
> My wireless connector is intel RJ45.
That is an ethernet connector -no such thing as a wireless connector (unless you're ralking about an adaptor}

BT Fon and BT Openzone are both services offered by the router, so you would seem to be connecting to the bt homehub - but perhaps you're saying that it's not validating the connection, so you need to find what sort of password encryption you need to use.

---

### Post by iclestu on 2011-06-02
did you get this up and running in the end? 

I have noticed a couple of oddities using BT's HomeHub at my own end (all easily circumvented tho). If I get a chance ill post about it but nit reminded me of your issue.

---

### Post by J*B on 2011-06-07
I am experiencing the same problem with a BT HomeHub 2 (Having to delete the computer name from the routers settings). This is a problem both wired and wireless.

Is this a BT HomeHub specific issue? Any similar issues with other routers? I keep finding more and more little bugs (This one, little snags with a Buffalo LiveStation) that make me want to get a proper router.

Or, is this an Ubuntu issue? I didn't have this issue with previous releases on exactly the same hardware and network equipment...

---

### Post by iclestu on 2011-06-07
> **J*B said:**
> I am experiencing the same problem with a BT HomeHub 2 (Having to delete the computer name from the routers settings). This is a problem both wired and wireless.

Is this a BT HomeHub specific issue? Any similar issues with other routers? I keep finding more and more little bugs (This one, little snags with a Buffalo LiveStation) that make me want to get a proper router.

Or, is this an Ubuntu issue? I didn't have this issue with previous releases on exactly the same hardware and network equipment...

maybe one of us should ring BT's helpful friends in the outsourced call centre to see if they know thier ar$e from their elbow.....

---

### Post by iclestu on 2011-06-07
> **J*B said:**
> 
Or, is this an Ubuntu issue? I didn't have this issue with previous releases on exactly the same hardware and network equipment...

I THINK i did, but it doesn't really happen often and is easy fixed so i may have just forgotten :)

---

### Post by J*B on 2011-06-07
I've done a bit of googling, someone suggested on AVForums that the router might be getting confused with different computer names trying to connect with the same MAC ID. I've used the Network Connections editor to change the MAC ID (increment the last digit by 1) for each of my network connections. After a couple of reboots it still seems to be holding. I'll post back when I've gone into Windows a couple of times and back to Ubuntu, see if it holds out. Hope this helps anyone who's stuck!

---

### Post by iclestu on 2011-06-08
oooo - i had been labouring under the misunderstanding that MAC addresses were unchangeable.... How did you do that then!?

I thought they were part of the hardware.....

---

### Post by J*B on 2011-06-08
I though that it was hard coded too, but if you open the Network Connections dialogue (accessible via the panel applet)and edit the connections it allows you to change the MAC ID. 

It seems strange to me that I've only seen this issue reports for Natty and HomeHub 2, and not any other combination of Ubuntu and router...

---

### Post by iclestu on 2011-06-08
> **J*B said:**
> I though that it was hard coded too, but if you open the Network Connections dialogue (accessible via the panel applet)and edit the connections it allows you to change the MAC ID. 

It seems strange to me that I've only seen this issue reports for Natty and HomeHub 2, and not any other combination of Ubuntu and router...

strange indeed.

I am using kubuntu and cant find any means to change the mac id... nemind, I hardly ever have reason to boot to windows these days (the only reason it is still on my hd is that i dont need the space and it wasnt free:mad:!).... I can live with it. 

Its just a bit baffling thats all...

---

### Post by mossontherock on 2011-06-08
> **coneill659 said:**
> I have downloaded ubuntu 11.04 and the internet does not connect to by bt home hub 2. 
 
The computer connects to bt Fon and bt openzone but not to the home hub. It recognises that the home hub is there and accepts the password but then tries to connect and fails.
 
I tried running the trouble shooting help section for wirless on ubuntu and it advised me to go on to a forum as the computer was not fully recognising my network adapter.
 
My wireless connector is intel RJ45.
 
Thanks :)
 
Here are my findings: 
Users on the internet are reporting that on dual boot systems, where linux and windows reside, linux will fail to pick up a network connection on a BTHomeHub if that same network device was recently used in windows. This apparently has only been an issue since an automatic rollout firmware update on BTHomeHub devices in May 2011.
 
The issue appears to be linked to the MAC and IP addresses and registered for each connected device.
 
My personal solution was to link another wireless router to the BTHomeHub, although this in itself didn't work for me.&nbsp; I also had to use the clone MAC address setting in the network connection setup, so that I could fake a different hardware MAC address for my network devices, which worked just fine swtiching between windows and ubuntu.

---

### Post by iclestu on 2011-06-08
> **mossontherock said:**
> Here are my findings: 
Users on the internet are reporting that on dual boot systems, where linux and windows reside, linux will fail to pick up a network connection on a BTHomeHub if that same network device was recently used in windows. This apparently has only been an issue since an automatic rollout firmware update on BTHomeHub devices in May 2011.
 
The issue appears to be linked to the MAC and IP addresses and registered for each connected device.
 
My personal solution was to link another wireless router to the BTHomeHub, although this in itself didn't work for me.&nbsp; I also had to use the clone MAC address setting in the network connection setup, so that I could fake a different hardware MAC address for my network devices, which worked just fine swtiching between windows and ubuntu.

thanks for clarifying that. For me, it is easier just to live with the workaround of deleting the machine from the router's network settings but that presupposes users have a different machine they can access the router's settings from....

Where did you find these btw? - i had a quick google and came up blank..

---

### Post by mossontherock on 2011-07-14
> **iclestu said:**
> thanks for clarifying that. For me, it is easier just to live with the workaround of deleting the machine from the router's network settings but that presupposes users have a different machine they can access the router's settings from....

Where did you find these btw? - i had a quick google and came up blank..

The issue and a solution is presented here:
[http://www.filesaveas.com/cgi-bin/forum/YaBB.pl?num=1306425958](http://www.filesaveas.com/cgi-bin/forum/YaBB.pl?num=1306425958)

---

