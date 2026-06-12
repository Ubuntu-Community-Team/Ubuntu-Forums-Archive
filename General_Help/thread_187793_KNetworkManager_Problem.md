---
title: "KNetworkManager Problem"
date: 2006-06-03
forum: General Help
---

### Post by oobe on 2006-06-03
I am trying to use WPA with KNetworkManager (KNM).

My wireless device is working fine.

KNM can see the network I want to connect to and when I click on it, it opens the form so I can enter the WPA key etc. When it actually goes to try and connect, it brings up the "Activating Wireless Network Connection" window and sits on 28% - "Activation stage: Configuring device.". From there nothing else happpens and it eventually gives up and goes back to wired.

It seems there is a problem with the frontend writing to or reading from whatever the config file is. Does anyone have a solution for this, or can at least tell me the file I can hand-edit which may get it to work?

Cheers,
oobe

---

### Post by oobe on 2006-06-03
I've seen other people have also had this problem, anyone found a solution yet?

oobe

---

### Post by NeoChaosX on 2006-06-04
What's your wireless chipset?

---

### Post by carlos1 on 2006-06-04
I have had this problem, trying to enable the second network device, and it hangs and goes back to the previous one. 

This is how I fixed it, although there may be better fixes.  Since no-one else has answered I'll give you my method. 

If you go into /etc/network there is a file called "interfaces". Under "The primary network interface" there should be a line "auto eth1" (or eth0,). Make sure it gives the id of the device you want to use (wireless) whether it is eth0 or eth1. Below that there is another line which should read (if you are connecting by dhcp): 
"iface eth1 inet dhcp" (change for eth0 if that fits.

After that I had to re-start the network (not sure the exact commands for that, but a reboot will always do if if all else fails) and then if the device is working properly it should come up as the automatic connection rather than wired.

---

### Post by oobe on 2006-06-04
I am using a HP/Compaq Presario x1000 with built in Intel 2100 chipset.

oobe

---

### Post by benobi on 2006-06-04
I might have an answer for you guys.
I have KNetworkManager working fine with WPA on my laptop.
If I remember, the way NetworkManager works now, you need to go in the interfaces files and remove some references to let NetworkManager  handle it.

So, open a terminal and type:

sudo kate /etc/network/interfaces 

Then in the interfaces files remove everything except those lines:

# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

Save the file and then restart your computer. That worked for me, and I hope it will for you.

---

### Post by mykrob on 2006-06-05
no luck for me.. Works fine for my wired connection, but not for my wireless connection..
I have a HP Pavilion ze2308 laptop.. My wireless is a broadcom 4318, configured to work with ndiswrapper.. It shows up as eth1. I can make it connect with 

dhclient eth1

through the command line.. 

But using KnetworkManager, i get the same stalling at 28% until it times out..

ANyone have a definite fix for this?

Thanks,
-myk robinson

---

### Post by mykrob on 2006-06-08
bump

---

### Post by mykrob on 2006-06-08
bump

---

### Post by Kieffer87 on 2006-08-27
Any luck on getting this figured out?

---

### Post by c4r1 on 2006-10-05
Same problem here on Edgy with a Dell TrueMobile 1400 WLAN.
Stops at 28%.

---

### Post by mjukis on 2007-01-07
I have the same problem running Kubuntu Edgy. Still no solution?

---

### Post by dutchman25 on 2007-01-26
I have the same problem using ndiswrapper for a bcm4319 card.  I can use dhclient perfectly to connect wirelessly, but I'd like to use Knetworkmanager for its "point n' click" capabilities.

---

### Post by dutchman25 on 2007-01-27
bump

---

### Post by Vomix on 2007-02-07
Same problem here, using Kubuntu 6.10 and a DLink-DWL G650+.

The led is on, but can't connect.

I've tried to install Ubuntu 6.10 & Network Manager, without succes...

---

### Post by mjukis on 2007-04-26
I bought a new router and have not had any problems anymore. I had a D-link but now i use a Asus with openWrt.

---

### Post by Red Knuckles on 2007-04-29
This worked for me in Linux Mint Bianca KDE. The KNetworkManager icon still pops up though I'd like to figure out how to stop that. Or I'll just hide it in system tray. Here's the instructions:

Disabling network manager in your gnome session will not work as that is just the 'notification area' for the network-manager service. To disable network-manager, either uninstall it (which will break ubuntu-desktop package) or do this:

Stop network manager...

sudo /etc/dbus-1/event.d/26NetworkManagerDispatcher stop
sudo /etc/dbus-1/event.d/25NetworkManager stop

Create two files with only the word 'exit' in them. These files are:

/etc/default/NetworkManager
/etc/default/NetworkManagerDispatcher

Reboot.

I know he's talking about Gnome but it worked for me in KDE. :lolflag: 
:guitar:

---

### Post by happypig on 2007-12-02
I've been trying to set this up today and have nearly got it. I'm at the stage where I can connect to
 the internet but it drops out after a while (might be due to inactivity or may be something else)

I'm running an eSystems laptop with Kubuntu 6.06. Wireless card is a Belkin f5d7050 USB jobbie 
connecting to a Belkin router using WPA-TKIP encryption. Hardware is ok as it works under windoze.

After getting the wireless adaptor running using ndiswrapper, I found two networks appearing in 
KNetworkManager, mine and the posh family over the road, so it's obviously working.

I then had several hours of trying to connect and getting stuck at 28%. After a lot of tries, I edited 
/etc/network/interfaces so that it read 

> auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto wlan0
iface wlan0 inet dhcp

#auto eth0
#iface eth0 inet dhcp

#auto eth1
#iface eth1 inet dhcp

#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp
 

Now it will connect for a while but drops out. I'm not sure why but maybe this will help someone else 
and they will get a more stable connection.

---

### Post by speedothebrief on 2007-12-08
I have a solution that worked for my bcm4318. I had the same trouble initially.

i had to enable the restricted driver for bcm43xx. I'm in Kubuntu, so this was in the Advanced System Settings.

It downloaded (from my wired network) the fwcutter stuff for the bcm cards automatically. It asked if I wanted to use a local file for the fw or an internet file, I just chose the default internet location.

When I booted up, I had to "turn on" the wireless card using the laptop's function keys. My little wireless indicator light appeared at this point (it never turned on before this point).

Then, KNM showed the wirless networks (I assume if I had waited long enough it would have found them automatically, but I was impatient and pulled up Konsole and typed "sudo iwlist scan" 3 or 4 times until my network appeared).

Then KNM configured the device perfectly (with 40bit WEP)!

I hope this works for you guys???

---

