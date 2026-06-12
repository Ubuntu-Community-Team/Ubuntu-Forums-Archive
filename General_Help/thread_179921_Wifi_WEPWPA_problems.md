---
title: "Wifi WEP/WPA problems"
date: 2006-05-21
forum: General Help
---

### Post by starkes on 2006-05-21
Hey

I've never been able to connect to a network with WEP encryption, and WPA is not even supported out of the box.

Am I the only one with the problem with WEP encrypted networks?

As for better WPA support, is there a timeline for when this will be available?

---

### Post by vayde on 2006-05-21
Logging on to WEP encrypted networks is pretty straightforward, but it does sometimes get messed up.  Are you using the command line?  or the gui?

---

### Post by starkes on 2006-05-22
i'm using gui

can anyone send me a link to a command line tutorial for networking in ubuntu?

---

### Post by vayde on 2006-05-22
I don't know of one, but there is probably one out there.  The gui works pretty well, but it often gets its signals crossed in my experience.

Here's what you need to do:

First of all, edit /etc/dhcp3/dhdhclient.conf and change the following two lines:

(you need superuser priviledges, and the lines are probably already there but commented out)

prepend domain-name-servers 206.191.207.250;  #use any name server you prefer
timeout 10; #You might have to experiment with this value, some of the dns servers are slower than others.

In my experience, sometimes you have trouble with the standard dns address that comes with some of the cheaper routers, prepending a known IP seems to fix it for me.

Lowering the timeout value will make the computer give up trying to connect sooner if it doesn't work.  The problems you are having with the gui seem to be related to or exacerbated by the length of time the machine doggedly waits for a connection.  (Then again, maybe its the user geting impatient- we all do it )  Either way fixing the time out value will make it much easier to try different settings and trouble shoot things

next you need to edit /etc/network/interfaces: 
(again you will need to be superuser)

Here's mine:
####################################################
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

# This is a list of hotpluggable network interfaces.
# They will be activated automatically by the hotplug subsystem.
mapping hotplug
	script grep
	map eth1

# The primary network interface
iface eth1 inet dhcp
	wireless-essid <Network Name goes here>
	wireless-key <WEP Key goes here> 

iface ppp0 inet ppp
provider ppp0

auto eth1

iface eth0 inet dhcp

########################################################

Once you are done with that, save the file and (assuming we are talking about eth1) type the following from the command line:

sudo ifup eth1

you should be golden.  type the following to  verify it's working:

ifconfig

this will bring up the specs on the interfaces.  Look for a valid IP on the second line after 'inet addr:'  if you see one, all should be well.

Bring the network back down (if you ever want to) with:

sudo ifdown eth1

If the above works, and it should, you will have a working network interface, with your WEP encryption.  You should be able to go back into the GUI and save the profile.

The GUI seems to have problems with profiles that are not active- or able to be active when you set them.  So in the future, if you want to set up a new profile, go to that location, load it with the GUI, verify that its working, and then save it.  Don't just save a bunch of profiles against future need- they won't always work when you try to use them

Good luck! Holler if you I wasn't clear enough.

P.S.  This will have tons more info for you:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by eyeballer786 on 2007-11-01
Vayde, I did exactly as you said. I did the terminal commands, and it says its working, yet it will not connect. I know it is my WEP because when i turned that off it worked fine. A little slow, but i can deal with that. I have been using Mac for my whole life so this is completely alien to me. I cant seem to find out whats out of place....

---

### Post by mikewhatever on 2007-11-01
Both wep and wpa work fine on my laptop. To get the options for wpa, right click on the nm icon next to the clock and select 'Connect to other networks', choose the one you want, and then you should get all the options for encryption.

Could it be that you are with Dapper? I do not know how well it supports wep/wpa.

---

