---
title: "nm-applet not showing in notification area"
date: 2010-05-17
forum: General Help
---

### Post by hwttdz on 2010-05-17
Fresh install (10.04), only the packages that I thought I needed.  nm-applet is running, but not appearing in the notification area of the panel.  Any ideas to make it appear there?

---

### Post by 2hot6ft2 on 2010-05-17
Right click on the top panel and select Add to Panel then select Notification Area and click Add then Close.
:guitar:

---

### Post by hwttdz on 2010-05-17
I'm sorry if I was unclear, the nm-applet is not showing in the notification area, which is present on the panel.  So there is a notification area.  And there is an nm-applet running.  But the nm-applet is not showing, in the notification area (or anywhere else), and this last part is the problem.

The notification area isn't showing anything other than a little vertical separator, I'm not sure if there should be more in the area?

---

### Post by hwttdz on 2010-05-17
Help?

---

### Post by Kenda on 2010-05-17
I am afraid I suffer from this little niggle as well. This and Gwibber not working are a bit of a nuisance.

---

### Post by hwttdz on 2010-05-17
Because of this I currently cannot connect to a wireless network.  A way to connect to a wireless network would also be helpful.

---

### Post by hwttdz on 2010-05-17
sudo gedit /etc/network/interfaces

you should have:
"auto lo
iface lo inet loopback

auto eth0

auto wlan0"

plus any comments (in the form of "# this is the primary network interface,..." ).  The important part seems to be not having any 
"iface wlan0 inet dhcp" lines or whatnot.  So after commenting out any iface lines (excepting the lo one), restart and the network manager should pick it up.  Also once the network manager picks it up it shows up in the notification area (solving the original problem).

---

### Post by fragos on 2010-05-17
make sur nm-applet, called "Network Manager," is started in Preferences-> Startup Applications. My startup Command: nm-applet --sm-disable

---

### Post by saeedov on 2010-07-13
just press add to panel ,then choose Notification Area ;)

---

### Post by _Jordy_ on 2010-07-29
> **saeedov said:**
> just press add to panel ,then choose Notification Area ;)
I've been messing with this problem for a while now and the above extreme simple solution did the trick for me :-) Found the solution here: [http://ubuntuforums.org/showpost.php?p=9581540&postcount=13](http://ubuntuforums.org/showpost.php?p=9581540&postcount=13)

---

### Post by kickinthethroat on 2010-08-15
> **hwttdz said:**
> sudo gedit /etc/network/interfaces

you should have:
"auto lo
iface lo inet loopback

auto eth0

auto wlan0"

plus any comments (in the form of "# this is the primary network interface,..." ).  The important part seems to be not having any 
"iface wlan0 inet dhcp" lines or whatnot.  So after commenting out any iface lines (excepting the lo one), restart and the network manager should pick it up.  Also once the network manager picks it up it shows up in the notification area (solving the original problem).

Thanks for this! This was a tricky problem for me to pin down.  I never would've thought my static IP iface line in /etc/network/interfaces would've caused network manager to not show up! Thanks again!

---

### Post by jdonbook86 on 2010-12-05
Just a note. If you happen to have multiple instances of the "notification area" running, it causes problems for the system. It doesn't know which one to use. I deleted all instances by right clicking on the little separation bars ( I had five!). Then I went back and added one instance of the notification area, and then all the indicator icons finally showed up. Hope this works for others.

---

### Post by jjmatt on 2010-12-05
So I may have a similar issue, though that solution doesn't work for me. nm-applet is loaded (shows up in ps aux) and my notification area (2.30.2) is loaded. I even tried making a new user to see if it would show up. It did not. I am running 10.10.

Any help would be appreciated.

---

### Post by djringjr on 2011-01-03
I have had this problem for months.  I have the solution.

Open terminal and do this:

sudo restart network-manager

You will now see the icon in the notification area.  If you do not see any wireless networks, just reboot.  You will see the icon as you should and this time you will be able to see the wifi networks.

Best wishes,

DR

---

### Post by filgy on 2011-01-15
I am having this same problem where the network icon does not show up in the notification area anymore. It was working fine until I upgraded from 10.04 to 10.10 a few days ago. I already tried all solutions listed in this thread (my /etc/network/interfaces file did not have any of the offending lines mentioned). nm-applet is running, etc etc.. 

It's starting to make me sick that if you don't do a fresh install every time a new release comes out, you will run into some upgrade bug. My company heavily depends on Ubuntu and we have some 9.10 machines (not my choice to pick a non LTS release) that will reach EOL in a few months. I almost tremble at the thought of upgrading them to 10.04 LTS. 

I HAVE found a work around, which doesn't make much sense to me and I also find it to be really really lame. The work around is to drop to console and do 'sudo killall Xorg' and let X reload then log back in. This almost *always* displays the network icon in the notification area (although sometimes the wireless icon is just a white block, but I can live with that fine since all the usability is there). This work around is unacceptable. 

I am on a Dell Latitude E6410 using the proprietary Broadcom and Nvidia drivers.

Thanks for any other ideas to permanently fix this problem. It is no problem when I am on a wired network b/c that just connects automatically, but I can not get on a wireless network without that icon.. Shouldn't there be another package or something I could install to manage wireless connections since right now, when the network icon is not showing up, I can't connect to any wireless network.

I would like to finally add that when I log into my account and X loads Gnome, it will *not* prompt me for my password to auto connect to the wireless network in range. When I kill Xorg then relog into X, it will then prompt me for the password and work fine (until the next restart, sleep, shutdown, etc).

---

### Post by djringjr on 2011-01-15
Do this in gnome-terminal:

```
sudo gedit /etc/network/interfaces

```
you should have:

```
"auto lo
iface lo inet loopback
```

No more than that.  The file will be reconfigured when network-manager restarts.

Now kill nm-applet, restart network manager and reboot:


```
sudo killall nm-applet
sudo restart network-manager
sudo reboot
```


That works for all of the people I know.

73

David

---

### Post by djringjr on 2011-01-15
If you want another way to connect to wireless networking, try ceni [http://www.mirrorservice.org/sites/sidux.com/sidux/debian/pool/main/c/ceni/ceni_2.21_all.deb]("http://www.mirrorservice.org/sites/sidux.com/sidux/debian/pool/main/c/ceni/ceni_2.21_all.deb") It is not in the regular Ubuntu repos, but it is an excellent program.  It has some dependencies so watch the error messages and use apt-get or aptitude to install the several dependencies required.

Also the command line network manager is in the repositories:  

```
 sudo apt-get install cnetworkmanager 
```

You should read the MANual on this to see how it us used, and perhaps write down the switches or options you need.

The simplest command is for a wifi that doesn't have any encryption:
```
 sudo cnetworkmanager --connect=SSID [CODE]

Where SSID is the name of the network.

The other commands which are already in Ubuntu are:

ifconfig iwconfig ifup ifdown

Which will bring up your connections.

Example:  If you had last connected your wifi connection but you're not connecte and your wifi was /dev/eth1 you can simply open a terminal and put in:

[CODE] sudo ifup /dev/eth1 
```

and ifup will bring up your wifi connection and connect to it using the previous (last) configuration.

I cannot tell you how many times ceni has rescued a computer that I've worked on that had connection problems.  I always install it.

Best wishes,

David

---

### Post by filgy on 2011-01-16
Sorry, double post.. Please see post below.

---

### Post by filgy on 2011-01-16
Thank you for your suggestions. /etc/network/interfaces had exactly what you stated it should have in it (I did try adding some extra things during my debugging but they were then removed). I still tried killing nm-applet and network-manager in the order you suggested and then rebooted to still no avail. My wireless interface is wlan1 and ifconfig is showing it up and everything, it is just not registering with my AP and getting assigned an IP/gateway/etc..

```
joel@jlesher:~$ ifconfig
eth2      Link encap:Ethernet  HWaddr 5c:26:0a:1a:4b:9b  
          inet addr:192.168.1.110  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::5e26:aff:fe1a:4b9b/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:19 errors:0 dropped:0 overruns:0 frame:0
          TX packets:49 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:2569 (2.5 KB)  TX bytes:7931 (7.9 KB)
          Interrupt:20 Memory:e9600000-e9620000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:480 (480.0 B)  TX bytes:480 (480.0 B)

wlan1     Link encap:Ethernet  HWaddr 58:94:6b:14:c8:6c  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

Trying to bring the wlan1 interface up and down like you suggested just gets it back to the results above (not connecting to the AP here that it is supposed to auto connect to nor prompting for my password to auto connect to it at all). So it shows the interface up already but not actually transmitting or pulling an IP or gateway, I suppose.

I'm going to check out the other utility for wireless that you mentioned since this quite has me disgusted. I will report back how that works out. Thanks a ton for your suggestions but unfortunately they did not work (let me kill Xorg process now and I bet wireless comes back then as I said in my original post... lame)

I think my new policy with Ubuntu is I will ONLY run LTS releases as they seem to be the only ones that get the loving necessary to not have little annoying bugs in them (since most corporations with contracts to Canonical are probably running LTS releases on their servers).

Finally, if anyone would have a launchpad link handy for this bug, could you please provide it? This thread is marked [SOLVED], but it obviously isn't for me and I would like to contribute to any bug report or reopen one if it was closed with what was already stated as the solution here (those solutions don't work for me ;p)

---

### Post by filgy on 2011-01-16
I just tried ceni. It found my wireless network fine and everything. I put in my WPA key, but it then says no DHCP offers were received from my router and exits.

```
joel@jlesher:~/Downloads$ sudo ceni
Configuring interface wlan1=wlan1 (inet)
run-parts --verbose /etc/network/if-pre-up.d
run-parts: executing /etc/network/if-pre-up.d/wireless-tools
run-parts: executing /etc/network/if-pre-up.d/wpasupplicant
wpa_supplicant: using default driver type: wpa-driver wext
wpa_supplicant: /sbin/wpa_supplicant -s -B -P /var/run/wpa_supplicant.wlan1.pid -i wlan1 -D wext -C /var/run/wpa_supplicant
Starting /sbin/wpa_supplicant...
wpa_supplicant: waiting for "/var/run/wpa_supplicant.wlan1.pid":  0 (max. 5)
wpa_supplicant: creating sendsigs omission pidfile: /lib/init/rw/sendsigs.omit.d/wpasupplicant.wpa_supplicant.wlan1.pid
wpa_supplicant: ctrl_interface socket located at /var/run/wpa_supplicant/wlan1
wpa_supplicant: configuring network block -- 0
wpa_supplicant: wpa-ssid "lesher" -- OK
wpa_supplicant: wpa-psk ***** -- OK
wpa_supplicant: wpa-mode 2 -- FAIL
wpa_supplicant: wpa-mode 2 -- FAIL
wpa_supplicant: enabling network block 0 -- OK

dhclient3 -e IF_METRIC=100 -pf /var/run/dhclient.wlan1.pid -lf /var/lib/dhcp3/dhclient.wlan1.leases wlan1
Internet Systems Consortium DHCP Client V3.1.3
Copyright 2004-2009 Internet Systems Consortium.
All rights reserved.
For info, please visit https://www.isc.org/software/dhcp/

Listening on LPF/wlan1/58:94:6b:14:c8:6c
Sending on   LPF/wlan1/58:94:6b:14:c8:6c
Sending on   Socket/fallback
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 5
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on wlan1 to 255.255.255.255 port 67 interval 8
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
run-parts --verbose /etc/network/if-up.d
run-parts: executing /etc/network/if-up.d/50firestarter
run-parts: executing /etc/network/if-up.d/avahi-autoipd
run-parts: executing /etc/network/if-up.d/avahi-daemon
run-parts: executing /etc/network/if-up.d/ntpdate
run-parts: executing /etc/network/if-up.d/openssh-server
ssh stop/waiting
ssh start/running, process 5628
run-parts: executing /etc/network/if-up.d/openvpn
run-parts: executing /etc/network/if-up.d/upstart
run-parts: executing /etc/network/if-up.d/wpasupplicant

Press Enter key to continue ...

```

Maybe I'll just try giving this laptop a static IP with ceni.. It appears to me to be finding my AP and starting initial registration with the WPA key and everything, correct? But then it is not offered an address from my router.. 

Any other thoughts or ideas?

EDIT: When I try putting in a static IP into ceni after it finds my AP and everything it loads it fine. ifconfig for wlan1 looks normal; showing the IP address, broadcast, gateway, etc. BUT when I try to ping or connect to the gateway it says destination host unreachable. So ceni still does not work even if I try to set a static IP and put in the proper network info.. 

EVERY upgrade I've done from one release to another for the past 4 or 5 times has resulted in some bug that drives me crazy. I love Ubuntu, but it is getting very very close to losing me as a user (as well as my company and support contracts with Canonical)..

---

### Post by djringjr on 2011-01-16
Hello,

Install hwinfo

```
sudo apt-get install hwinfo
```

Attach the file hwinfo.txt to your message:
```

sudo hwinfo > hwinfo.txt
```

I agree with you on the LTS Ubuntu, just install the "backports" repos.
Here is my customised /etc/apt/sources.list file which I use for Vinux the Ubuntu for sight impaired users.

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

# Repositories supporting vinux packages.
# If you are willing to help test new Vinux packages, uncomment the following:
# deb http://ppa.launchpad.net/vinux/vinux-lucid-testing/ubuntu lucid main
# deb-src http://ppa.launchpad.net/vinux/vinux-lucid-testing/ubuntu lucid main
deb http://ppa.launchpad.net/vinux/maverick-testing/ubuntu maverick main
deb-src http://ppa.launchpad.net/vinux/maverick-testing/ubuntu maverick main
deb http://www.geekconnection.org/remastersys/repository karmic/
# deb http://ppa.launchpad.net/vinux/vinux-lucid/ubuntu lucid main
# deb-src http://ppa.launchpad.net/vinux/vinux-lucid/ubuntu lucid main
deb http://ppa.launchpad.net/vinux/maverick/ubuntu maverick main
deb-src http://ppa.launchpad.net/vinux/maverick/ubuntu maverick main

# Get Deb Packages 

# deb http://archive.getdeb.net/ubuntu maverick-getdeb apps
# deb http://archive.getdeb.net/ubuntu lucid-getdeb apps
# deb-src http://archive.getdeb.net/ubuntu lucid-getdeb apps

# Get Deb Package Mirror
# deb http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
# deb-src http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps

deb http://mirrors.dotsrc.org/getdeb/ubuntu maverick-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu maverick-getdeb apps

# MOC Command Line Multimedia Player
#deb http://www.lxtec.de/debarchiv unstable main
#deb-src http://www.lxtec.de/debarchiv unstable main

```


More later - we will fix this.

David

---

### Post by djringjr on 2011-01-16
Hello,

Install hwinfo

```
sudo apt-get install hwinfo
```

Attach the file hwinfo.txt to your message:
```

sudo hwinfo > hwinfo.txt
```

I agree with you on the LTS Ubuntu, just install the "backports" repos.
Here is my customised /etc/apt/sources.list file which I use for Vinux the Ubuntu for sight impaired users.

```
# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

# Repositories supporting vinux packages.
# If you are willing to help test new Vinux packages, uncomment the following:
# deb http://ppa.launchpad.net/vinux/vinux-lucid-testing/ubuntu lucid main
# deb-src http://ppa.launchpad.net/vinux/vinux-lucid-testing/ubuntu lucid main
deb http://ppa.launchpad.net/vinux/maverick-testing/ubuntu maverick main
deb-src http://ppa.launchpad.net/vinux/maverick-testing/ubuntu maverick main
deb http://www.geekconnection.org/remastersys/repository karmic/
# deb http://ppa.launchpad.net/vinux/vinux-lucid/ubuntu lucid main
# deb-src http://ppa.launchpad.net/vinux/vinux-lucid/ubuntu lucid main
deb http://ppa.launchpad.net/vinux/maverick/ubuntu maverick main
deb-src http://ppa.launchpad.net/vinux/maverick/ubuntu maverick main

# Get Deb Packages 

# deb http://archive.getdeb.net/ubuntu maverick-getdeb apps
# deb http://archive.getdeb.net/ubuntu lucid-getdeb apps
# deb-src http://archive.getdeb.net/ubuntu lucid-getdeb apps

# Get Deb Package Mirror
# deb http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
# deb-src http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps

deb http://mirrors.dotsrc.org/getdeb/ubuntu maverick-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu maverick-getdeb apps

# MOC Command Line Multimedia Player
#deb http://www.lxtec.de/debarchiv unstable main
#deb-src http://www.lxtec.de/debarchiv unstable main

```


More later - we will fix this.

David

---

### Post by djringjr on 2011-01-16
Hello,

Install hwinfo

```
sudo apt-get install hwinfo
```

Attach the file hwinfo.txt to your message:
```

sudo hwinfo > hwinfo.txt
```

I agree with you on the LTS Ubuntu, just install the "backports" repos.
Here is my customised /etc/apt/sources.list file which I use for Vinux the Ubuntu for sight impaired users.

```

# deb cdrom:[Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)]/ maverick main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ maverick main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick universe
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick multiverse
deb http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ maverick-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu maverick partner
deb-src http://archive.canonical.com/ubuntu maverick partner

## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu maverick main
deb-src http://extras.ubuntu.com/ubuntu maverick main

deb http://security.ubuntu.com/ubuntu maverick-security main restricted
deb-src http://security.ubuntu.com/ubuntu maverick-security main restricted
deb http://security.ubuntu.com/ubuntu maverick-security universe
deb-src http://security.ubuntu.com/ubuntu maverick-security universe
deb http://security.ubuntu.com/ubuntu maverick-security multiverse
deb-src http://security.ubuntu.com/ubuntu maverick-security multiverse

# Repositories supporting vinux packages.
# If you are willing to help test new Vinux packages, uncomment the following:
# deb http://ppa.launchpad.net/vinux/vinux-lucid-testing/ubuntu lucid main
# deb-src http://ppa.launchpad.net/vinux/vinux-lucid-testing/ubuntu lucid main
deb http://ppa.launchpad.net/vinux/maverick-testing/ubuntu maverick main
deb-src http://ppa.launchpad.net/vinux/maverick-testing/ubuntu maverick main
deb http://www.geekconnection.org/remastersys/repository karmic/
# deb http://ppa.launchpad.net/vinux/vinux-lucid/ubuntu lucid main
# deb-src http://ppa.launchpad.net/vinux/vinux-lucid/ubuntu lucid main
deb http://ppa.launchpad.net/vinux/maverick/ubuntu maverick main
deb-src http://ppa.launchpad.net/vinux/maverick/ubuntu maverick main

# Get Deb Packages 

# deb http://archive.getdeb.net/ubuntu maverick-getdeb apps
# deb http://archive.getdeb.net/ubuntu lucid-getdeb apps
# deb-src http://archive.getdeb.net/ubuntu lucid-getdeb apps

# Get Deb Package Mirror
# deb http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps
# deb-src http://mirrors.dotsrc.org/getdeb/ubuntu lucid-getdeb apps

deb http://mirrors.dotsrc.org/getdeb/ubuntu maverick-getdeb apps
deb-src http://mirrors.dotsrc.org/getdeb/ubuntu maverick-getdeb apps

# MOC Command Line Multimedia Player
#deb http://www.lxtec.de/debarchiv unstable main
#deb-src http://www.lxtec.de/debarchiv unstable main

```


More later - we will fix this.

David

---

### Post by filgy on 2011-01-17
Forum won't let me upload my entire hwinfo.txt, but I emailed it to djringjr.. Funny thing is, I use a Dell docking station at work with this laptop, and wm-applet and wireless always pretty much works when docked. But I did the upgrade from 10.04 to 10.10 when the laptop was NOT in the dock.. It's very strange. I may have to downgrade to 10.04 LTS..

EDIT: I should also add that someone I work with upgraded from 10.04 to 10.10 with no problems on a dell latitude E6400. Mine is the same as his except a E6410..

---

### Post by filgy on 2011-01-18
I grabbed djringjr's sources.list and updated packages to be inline with that. After doing this I rebooted. Same problem. I figured I'd install KDE and try that. Wifi didn't work in KDE, either. I then made a usb stick netinstall to reinstall 10.10 with. I started that but then canceled. When I rebooted I booted into 'Ubuntu Desktop (Safe Mode)' instead of just 'Ubuntu Desktop'. I then logged right out of Safe Mode and back into the normal Ubuntu Desktop environment and it HAS BEEN WORKING (knock on wood) so far through 2 reboots. I'm going to try a few more reboots and report if it is still working.

If it continues to work, I have no idea at all what fixed it. Unless a package update sneaked itself in or something. Either way, so far, it appears to be back to normal. I will update this post after I shutdown/reboot at least 10 times w/out hopefully anymore problems.

Thanks for all the help.

---

### Post by adduds on 2011-03-17
> **hwttdz said:**
> sudo gedit /etc/network/interfaces

you should have:
"auto lo
iface lo inet loopback

auto eth0

auto wlan0"

plus any comments (in the form of "# this is the primary network interface,..." ).  The important part seems to be not having any 
"iface wlan0 inet dhcp" lines or whatnot.  So after commenting out any iface lines (excepting the lo one), restart and the network manager should pick it up.  Also once the network manager picks it up it shows up in the notification area (solving the original problem).

buddy THANKS! i wish i could buy you a beer for this one!

---

### Post by djringjr on 2011-03-17
I found a setting and I'm not that good with networking that changed a value of "manage networks" to true.  (I think 1 is true, 0 is false).

Change this, then

sudo killall nm-applet
sudo stop network-manager

Often various killall nm-applet, stop network-manager, start n
And I've rebooted and it worked fine.

[http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html](http://www.ubuntugeek.com/possible-solutions-to-fix-the-missing-network-manager-icon-in-ubuntu-9-10.html)

I promise next time I have no network for a few days and get the solution I will write it down.

David

---

### Post by wonder1 on 2011-11-07
Thanks hwttdz !

I had the same problem and your suggestion (post #7) solved my problem :

> 
sudo gedit /etc/network/interfaces

you should have:
"auto lo
iface lo inet loopback

auto eth0

auto wlan0"

plus any comments (in the form of "# this is the primary network interface,..." ). The important part seems to be not having any 
"iface wlan0 inet dhcp" lines or whatnot. So after commenting out any iface lines (excepting the lo one), restart and the network manager should pick it up. Also once the network manager picks it up it shows up in the notification area (solving the original problem).

---

