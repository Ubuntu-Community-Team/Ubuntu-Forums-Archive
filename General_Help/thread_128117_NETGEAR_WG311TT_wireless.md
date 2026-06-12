---
title: "NETGEAR WG311TT wireless"
date: 2006-02-10
forum: General Help
---

### Post by kyoushu on 2006-02-10
I currently use Windows XP SP2.  I love the livecd of ubuntu and I wish to install it on my computer.  The only thing is that my wireless internet does not work.  I don't know much of the hardware specs but I use a netgear wireless router.  If anyone can help in getting ubuntu to have wirless internet using the netgear wireless router that would be great.  I have no experience with the Linux Terminal at all, and I do understand I need to learn to use it to effeciantly use ubuntu.  So, expect me to be a "noob". Any help would be much appreciated.

---

### Post by torf on 2006-02-10
It would be helpful to know what kind of wireless card you are using.  With your setup, the easiest way to do this is probably to check under Device Manager in Windows (Control Panel --> System --> Hardware --> Device Manager --> Network Adapters).  Some other useful information can be found by opening a terminal under Linux, and typing "dmesg". If you can't find your card being detected in there (most likely towards the end), post it here and I'll have a look.

To dump this output to a text file in the home directory:
> dmesg > ~/dmesg_output.txt

To just manually scroll through it:
> dmesg | less 

Also, do you have encryption enabled on your router?  If so, you'll need to enable this under Linux to get the card working:
System --> Administration --> Networking --> Select your Wireless card if it's there --> Properties --> Check "enable this connection" , fill in the ESSID and enter the key.  Select DHCP for your connection settings unless you assign static IP's.

If you think your card is being detected, but just not connecting to the WAP, Try opening a terminal and typing "iwconfig" and post results here so I can take a look.

---

