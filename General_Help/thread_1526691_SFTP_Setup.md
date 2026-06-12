---
title: "SFTP Setup"
date: 2010-07-08
forum: General Help
---

### Post by LJNS on 2010-07-08
Hello,

I am a bit new at ubuntus. Here is what I would like to do, I want to set up my server to use SFTP, I am trying to assign the server a dedicated IP address I have a block through my isp so I need this server to get one. Also when I type in /etc/network/interfaces, it says permission denied. 

Once I get all that setup I need some help with setting up users.

Thank you.

---

### Post by The Cog on 2010-07-08
Do you have a GUI? If so, the eaasiest way to set up a permanent address is to go to the little wireless icon, right-click and choose edit connections.

If not, you can edit /etc/network/interfaces (or do other things that need root permission) by putting sudo in front of the command, e.g. > sudo nano /etc/network/interfaces. If you want to launch a GUI editor or nautilus explorer, gksudo in front like this:
> gksudo nautilus
gksudo gedit /etc/network/interfaces
In the GUI, users are edited with System->Administration->Users and groups. I'm not sure about command-line user editing.

---

### Post by LJNS on 2010-07-09
ok i got gnome on here, so I don't quite know were to go im a total noob to this.

---

### Post by The Cog on 2010-07-09
OK. **Right-click** the network icon (see the picture attached) and edit the Auto eth0 entry, changing it to static IP.

The icon might be on the bottom of your screen instead of the top - I can't remember where it goes by default. Also, if the wired ethernet isn't working, the icon might look different - a series of concentric arcs like a sonar perhaps.

---

### Post by LJNS on 2010-07-09
Theres my issue, i searched and I don't have the Network Manager Icon, is there some were I can enable it?

---

### Post by The Cog on 2010-07-09
I don't know. But you should also be able to find the configuration in the menus under System->Preferences->Network Connections.

---

### Post by LJNS on 2010-07-12
Alright got into the /etc/network/interface area in a terminal 

I got some instructions online i edit the seting to the following:

#The loopback network interfaces 
auto lo 
iface lo inet loopback

#The primary network interfaces
auto eth0
interface eth0 inet static
address ( one of my ip addresses)
netmask 
gateway

---

