---
title: "The Verge of Tears: Wireless, Dapper and Shaun"
date: 2006-06-18
forum: General Help
---

### Post by blue_thunder on 2006-06-18
I've been trying through the day to set up wireless in Dapper after having no trouble at all in Breezy, but all to no avail. It detects the "bcmwl5" driver and I enter my ssid and WEP key, but when i try to connect (dhcp) it takes a while and says the connection is active, but when I attempt to start up firefox, no luck.

iwconfig yields:

```
sthehi07@dhcp81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11a/b/  ESSID:"belkin54g"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
```

Also, I can't ping my router.

Any help would be much appreciated.

-Shaun

---

### Post by bollix47 on 2006-06-18
See if anything [here]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=bcmwl5") helps.

---

### Post by dubbreak on 2006-06-18
I have a card with the same chipset and I am running dapper. Have you tried manually configuring the card? (for some reason recently the config applet hasn't been working for me on that card).

Try:
sudo iwconfig eth1 essid yourroutersidhere
sudo dhclient eth1

You may also have to try:
sudo iwconfig eth1 mode managed

And at school where there are many routers with the same id I do:
sudo iwconfig eth1 ap any

oohh forgot to add, if you have to run the other items you will probably have to attempt to grab an ip again. I assume you already have the router setup for that card, so it isn't rejecting it based on MAC adress or anything like that.

---

### Post by blue_thunder on 2006-06-18
The problem with that guide is your computer needs internet access to download the needed programs from the repositories...without the connection, that FAQ is worthless. My laptop doesn't have any possible connectionoutside of the wireless, so I need to get it working withoutan active connection. I can't use synaptic of apt-get.

---

### Post by blue_thunder on 2006-06-18
Alright Dub. I tried a few of your recommendations. dhclient yielded:

```
sthehi07@dhcp81:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

SIOCSIFFLAGS: No such file or directory
SIOCSIFFLAGS: No such file or directory
Listening on LPF/eth1/00:90:4b:2f:4a:bb
Sending on   LPF/eth1/00:90:4b:2f:4a:bb
Sending on   Socket/fallback
receive_packet failed on eth1: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 20
send_packet: Network is down
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
send_packet: Network is down
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

```

Do you have any other ideas?

---

### Post by blue_thunder on 2006-06-18
Still completely lost. I really don't want to go back to windows, but I don't think I have too many choices as it is. I need to use the laptop, and I can't figure out the wireless.

---

### Post by blue_thunder on 2006-06-18
When I try to connect to my wireless network via wifi-radar, it just keeps telling me it can't find the IP. Am I doing something really simple wrong?

---

### Post by joshrobinson on 2006-06-18
[QUOTE=blue_thunder]When I try to connect to my wireless network via wifi-radar, it just keeps telling me it can't find the IP. Am I doing something really simple wrong?[/QUOTE]


try 
```
sudo ifconfig eth1 up
```
then your dhcp
```
sudo dhclient eth1
```

make sure that you have your essid set also

---

### Post by DarkOx on 2006-06-18
I'm using the bcmwl5 driver, and it doesn't work right out of the  box. There are two ways to get it working:

a) Install the correct firmware, using a program called bcm43xx-fwcutter. It can be installed via Synaptic or Adept, but I've never used it myself, so I'm afraid I can't help you with it.

b) Use ndiswrapper. It will be the same as in Breezy, only now you must blacklist your current bcmwl5 driver that isn't working. This can be done by adding the line "blacklist bcm43xx" to /etc/modprobe.d/blacklist. Now, when you reboot, the non-functioning bcmwl5 driver won't load, and ndiswrapper will.

---

### Post by blue_thunder on 2006-06-19
Thanks to both of you first of all. I have yet to try DarkOx's advice, but will shortly.

To Josh  Robinson:

"sudo ifconfig eth1 up" yielded:

```
SIOCSIFFLAGS: No such file or directory.
```

---

### Post by blue_thunder on 2006-06-19
To Dark Ox::

How would I reinstall bcmwl5 with ndiswrapper after blacklisting it? Also is the "xx" of bcm43xx replaced with anything?

---

### Post by blue_thunder on 2006-06-19
Alright. I added "blacklist bcm43xx" to my etc/modprobe.d/blacklist file, and I rebooted and things changed. Now, my wireless lists itself under "wlan0" instead of "eth1," and it says it's active when i go to System-Networking, but still no luck. Ndiswrapper was listing bcmwl5 as my driver still, so I typed ndiswrapper -e bcmwl5. Now, though, when I tried to reinstall bcmwl5 in ndisgtk, it wouldn't work saying:

```
modprobe config already contains alias directive
```

Of further note, iwconfig now yields:

```
sthehi07@dhcp81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:-2147483648 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

I think this is going in the right direction, I just need to know where to go next? How do I fix this bcmwl5 driver program with modprobe?

---

### Post by Zodiac on 2006-06-19
ha ha welcome to hell..... there are no wires in hell!!!!!!!

---

### Post by blue_thunder on 2006-06-19
Though humorous, that's not exactly helpful. Have any ideas for the driver business?

---

### Post by panurge77 on 2006-06-19
The modprobe error is probably only telling you ndiswrapper is already loaded, so no big deal. What I had to do to set my card working correctly with ndiswrapper was changing some lines on /etc/network/interfaces
My card will only connect if I give the key before the essid, so I changed

iface wlan0 inet dhcp
wireless-essid yourssid
wireless-key yourkey here

to

iface wlan0 inet dhcp
wireless-key open s:yourkeyhere
wireless-essid yourssid

Also I had to tell it it's an open network because retricted was the default, and the s: is about an ASCII key... That solved my problems, but it was another card, so I don't know if that applies to yours...

---

### Post by blue_thunder on 2006-06-19
I changed /etc/network/interfaces, but no luck. I really think it's a driver problem, but I'm not sure how to fix it. How would I find my IP again if I wanted to? Like, IP, subnet, gateway...?

---

### Post by blue_thunder on 2006-06-19
GOD DA****!!! Things have taken a sudden and unexpected turn for the worse. Wlan0 is now completely missing, iwconfig doesn't even show it anymore, neither does System->Networking. What can I do to fix myself?

I have the driver, but I can't reinstall it because modprobe says the alias is already there.

---

### Post by blue_thunder on 2006-06-19
OK. I installed bcmwl5 and bcmwl5a, and ndisgtk shows them present, but now it says the hardware isn't present. An hour ago, the hardware was present.

---

### Post by blue_thunder on 2006-06-19
I took bcm43xx off the blacklist, and wlan0 now shows up, but it says the hardware still isn't present.

---

### Post by blue_thunder on 2006-06-19
any solutions for hardware not present?

---

### Post by nickdr on 2006-06-19
you said it worked with breezy correct???

why dont you install breezy and then just dist-upgrade, assuming you did a fresh install of dapper???

---

### Post by blue_thunder on 2006-06-19
it's more of "i'm trying to get it working in dapper alone" sort of thing.

---

### Post by DarkOx on 2006-06-19
blue_thunder, here's how I managed to get wireless working in Kubuntu (though since I mostly used command-line, it should work the same in Ubuntu).

First, I had to install a program called "ndiswrapper-utils". If your Ubuntu computer has access to wired internet (in my case, I have a laptop, so moving the thing downstairs and connecting a cable was trivial), you can open up Synaptic (at the top of GNOME screen, select "Desktop", then "Administration", then "Synaptic Package Manager") or Adept (from the KDE menu, select "System", then "Adept"), search for "ndiswrapper-utils", and install it.

If this program doesn't appear, then perhaps the repositories (places on the 'net where Ubuntu programs are stored so they can be downloaded by users) that contain it have been disabled. If this is the case, open up a terminal, and if you're using Ubuntu type: 

> sudo gedit /etc/apt/sources.list

if you're using Kubuntu, type:

> kdesu kwrite /etc/apt/sources.list

either way, make sure that the lines "deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted" and "deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) dapper main restricted" do not have a "#" symbol in front of them. If they do, remove it. After this, type in a terminal

> sudo apt-get update

After this, the packages should appear in Synaptic or Adept, and you can install them.

If you don't have internet access from your Ubuntu computer, you can download the package from [http://packages.ubuntulinux.org/dapper/misc/ndiswrapper-utils](http://packages.ubuntulinux.org/dapper/misc/ndiswrapper-utils). Transfer it onto your Ubuntu computer, and right-click the file. The option to install it should be there. It will ask you for your password, and automatically install it. I don't think the package has any dependencies (other packages it needs to run) that aren't pre-installed on Ubuntu, but I'm not sure. If you get an error, either post back here, and I'll try to help you through it or use the above method for installing ndiswrapper.

Now that ndiswrapper is installed, you can use it via the command line. First, you need the bcmwl5.inf and bcmwl5.sys files that came with your wireless card. These can be found on the CD that came with your card, or from the website of the company that made your card. Copy these files somewhere convenient, like "/home/username/drivers". Now open up a terminal, and type:

> cd /home/username/drivers

or wherever you saved the files to. Then type in the terminal:

> ndiswrapper -i bcmwl5.inf

then type:

> ndiswrapper -l

something like: "filename          driver present, hardware present" should appear. If it does, it's ok to go on. Type:

> sudo ndiswrapper -m

put in your password, and then type:

> sudo depmod -a

then:

> sudo modprobe ndiswrapper

to make sure the module will automatically load everytime, type

> sudo gedit /etc/modules

if you're using Ubuntu or

> kdesu kwrite /etc/modules

if you're using Kubuntu. Either way, add the line "ndiswrapper" to the end of the file and save. Finally, I had to blacklist the bcm43xx driver, by typing:

> sudo gedit /etc/modprobe.d/blacklist

or

> kdesu kwrite /etc/modprobe.d/blacklist

and adding the line "blacklist bcm43xx". Save, exit and reboot your computer. Your wireless card should now be working. I believe that networkmanager and wpasupplicant are pre-installed on Ubuntu (though I'm not sure, as I use Kubuntu, which doesn't have networkmanager by default). With these programs you should be able to access a wireless network using either WPA or WEP security without editing any configuration files.

---

### Post by blue_thunder on 2006-06-20
Ox,

I really appreciate how much time you put into this. Not many have been willing to help, and I understand I've been kind of a pain in the ***, so I just wanted to thank you very much. I've followed all your directions, and I'm about to reboot. The only slight problem I ran into was after I typed "ndiswrapper -m" it yielded, "modprobe config already contains alias directive." I don't know if that's a problem or not, I'm going to restart now, so we'll find out. 

Thanks again. I'll post my results.

---

### Post by blue_thunder on 2006-06-20
AH! IT WORKED!! After a bit of fiddling with wifi-radar, it's up and running. I can't thank you enough Ox. Please contact me.

---

