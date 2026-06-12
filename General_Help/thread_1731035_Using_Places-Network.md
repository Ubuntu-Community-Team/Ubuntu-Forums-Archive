---
title: "Using Places-Network"
date: 2011-04-16
forum: General Help
---

### Post by rsnow on 2011-04-16
Unable to mount location
When I use the method of clicking on Places/Network, the Network window opens displaying the icon for my computer and an icon for Windows Network.

When I click on the Windows Network icon the display changes to show an icon for MSHOME (my Windows computers) and an icon for WORKGROUP (my Ubuntu computers).

Clicking on the MSHOME icon results in a pop up message saying "Opening MSHOME , You can stop this operation by clicking cancel." Then, I get a message saying "Unable to mount location.
Failed to retrieve share list from server."

Clicking on the WORKGROUP icon brings up icons for my Ubuntu computers. Clicking on any of these gives me the same messages that I get on the MSHOME icon...."Opening and Unable to mount".

I can access and share files on the other computers by using the method of clicking on Places/Connect to Server and then selecting "Windows share" from the drop down menu and typing in the ip address.

Can someone tell me what I need to do to make it possible to connect and share by using "Places/Network" , to be able to open and mount the locations?

---

### Post by kseise on 2011-04-17
If they are Ubuntu (or any Linux) machines you have to make sure that you install and configure SAMBA to get them to show up in a Windows network.  Nautilus has the ability builtin to browse them, but if the other boxes aren't configured to share anything with SAMBA, there is simply nothing to connect to, so you will get the message you are seeing.  

Try this thread for starters.  It might be a little outdated by now, but it should work.

[http://ubuntuforums.org/showthread.php?t=202605](http://ubuntuforums.org/showthread.php?t=202605)

UPDATE:
Woops, sorry, I just found this [https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba](https://help.ubuntu.com/community/Samba?action=show&redirect=SettingUpSamba)

---

### Post by rsnow on 2011-04-18
Thanks for response. I'll see what I can do with the information provided.

---

### Post by rsnow on 2011-04-21
I have read over the material at the link provided and honestly I am more confused now. It seems they say that what is automatically installed with Ubuntu 8.04> should work just by clicking Places/Network. Then they go on to include instructions for installing samba.

I have checked on my Ubuntu 10.10 machines and they each show the following installed:
samba: Samba/CIFS file print, and login server for Unix
samba common: Common files used by both the Samba server and client
samba\common-bin: Common files used by both Samba server and client
libwbclient0: Samba winbind client library
python-smbc: Python bindings for Samba clients (libsmbclient)
smbclient: Command-line SMB/CIFS clients for Unix
nautilus-share: Nautilus extension to share folders using Samba
libsmbclient: Share library for communication with SMB/CIFS servers
gnome-system-tools: Cross-platform configuration utilities for GNome

I can connect to the Ubuntu machines from my Windows machine but not the other way around. Well, I can connect to Windows machine with 'connect to server and entering the ip address. So I guess I'll have to live with that arrangement. But thanks for trying to help.

---

### Post by kseise on 2011-04-21
I can't walk you through it, because I don't have it setup, but I think you might have to go back and check the configuration options.  Simply installing the software doesn't setup the server.  There is something about exporting shares and stuff.  I remember it being straightforward when I last set it up.

---

### Post by rsnow on 2011-04-22
I understand what you're saying and I don't mind working on the command line (when I have a clue as to what I am doing). Actually, I am in the process of going through Wm. Shotts' book trying to learn more about using the command line.

Having said that, it seems odd to me that using network tools offered in System/Admin and System/Preferences doesn't give a more straightforward way to accomplish all that needs to be done.

Well, I'm slow in my old age but I'll keep trying.

---

### Post by rsnow on 2011-04-30
I'm going to use the 'connect to server' function and forget about using Places/Network. I have another issue that is bugging me right now. So, will close this thread and see if I get some help on the other problem.

---

