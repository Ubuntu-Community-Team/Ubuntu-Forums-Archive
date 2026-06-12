---
title: "Atheros driver support help needed plz"
date: 2006-02-12
forum: General Help
---

### Post by Shivanry on 2006-02-12
Okay, totally new to this. I'm an MCSE, but Linux is a new beast to me. I am attempting to get my Atheros AR5001X+ 54mbps (802.11a, b,g) to start working. I have retrieved the driver from madwifi.org. Furthermore, I have downloaded ndiswrapper and have checked the list to make sure my Atheros AR5001X+ 54mbps is supported, and it is.
   
   My questions are:

1. I dl'ed these on my windows based pc. I can just thumbdrive them to my pc with Ubuntu yeah? No extra drivers needed for that?

2. How do I install Ndiswrapper and get my driver installed?

   I know that this thread is a replica of a 1000 other threads. I have done a lot of reading, i just need this last little push to bridge my research to application....thank you very much in advance!

---

### Post by Shivanry on 2006-02-12
I just found this on the Ubuntu Wiki (about atheros drivers):

[I]Works out of the box in Breezy via the madwifi linux-restricted-kernel that is included by default. No tweaking required[/I

  What does this above statement mean? I think this might help me if i can just decrypt its puzzling labrynth of information...

  thanks again!

---

### Post by jakethesnake on 2006-11-06
I need help with this as well. Same deal as Shivanry. 

Toshiba Atheros AR5001X wifi connection is going no where...

---

### Post by Ramses de Norre on 2006-11-06
```
sudo aptitude install linux-restricted-modules-generic
```
(Substitute "generic" by "386" when using linux-386)

This will give you the linux-restricted-modules and the atheros driver should load at start up, I have an atheros myself and it always worked out of the box from breezy.

Is your card listed in network-admin? If so the driver is working, otherwise post the output of these commands:```
iwconfig
lsmod|grep ath
```

---

### Post by jakethesnake on 2006-11-06
Here is my output:
```

jake@jake-laptop:~$ sudo aptitude install linux-restriced-modules-386
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-restriced-modules-386"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jake@jake-laptop:~$ sudo aptitude install linux-restriced-modules-generic
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-restriced-modules-generic"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jake@jake-laptop:~$ sudo aptitude install linux-restriced-modules-386
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-restriced-modules-386"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jake@jake-laptop:~$ clear

jake@jake-laptop:~$ sudo aptitude install linux-restriced-modules-386
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-restriced-modules-386"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jake@jake-laptop:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11b  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:19:59:EF
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=61/94  Signal level=-34 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

jake@jake-laptop:~$ Ismod|grep ath
bash: Ismod: command not found
jake@jake-laptop:~$ lsmod|grep ath
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample
jake@jake-laptop:~$ clear

jake@jake-laptop:~$ sudo aptitude install linux-restriced-modules-386
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Couldn't find any package whose name or description matched "linux-restriced-modules-386"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
jake@jake-laptop:~$ iwconfig
lo        no wireless extensions.

ath0      IEEE 802.11b  ESSID:"linksys"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:19:59:EF
          Bit Rate:11 Mb/s   Tx-Power:18 dBm   Sensitivity=0/3
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=60/94  Signal level=-35 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

jake@jake-laptop:~$ lsmod|grep ath
ath_pci                80540  0
ath_rate_sample        17160  1 ath_pci
wlan                  144924  4 wlan_wep,ath_pci,ath_rate_sample
ath_hal               148816  3 ath_pci,ath_rate_sample
jake@jake-laptop:~$

```

---

### Post by Ramses de Norre on 2006-11-06
First: you've already got the atheros driver and it's working, you just need to configure your network settings correctly.

Secondly: I think you've got a wrong sources.list because you should be able to install the restricted modules, they are in restricted.
But they aren't needed for the atheros driver I see.

Go to System > administration > networking to configure your network.

---

### Post by jakethesnake on 2006-11-06
.

---

### Post by jakethesnake on 2006-11-08
I've changed the configurations multiple times, something is not right. Could my router configurations be my problem, fyi I changed them multiple times too to match my settings with ubuntu and still no joy? :(

---

### Post by realitycomputer on 2007-02-23
I find the gui wifi configs to be unreliable at best.
I don't know why, I usually get connection failed - maybe it's just my AP's!?

Why don't you just configure it manually.

Tell it the name of your access point:
```
sudo iwconfig ath0 essid YOUR-ACCESS-POINT-NAME
```

Tell it your WEP key (if any):
```
sudo iwconfig ath0 key YOUR-WEP-KEY
```

Apply for a dhcp lease (IP address, DNS server, etc):
```
dhclient ath0
```

You can now test connectivity by simply pinging your AP's IP and/or somewhere like [www.google.com](www.google.com).

Why not put those lines into a text file, name it something like wifi-on.sh, save it in your home dir and launch the wifi link using that in future.
You'll need to make the file executable. If you're still very new to *nix, easiest method is r.click on the file ---> properties ---> permissions ---> tick "is executable"
Now all you need do is open a console and type: ./wifi-on.sh

If you've messed around with the AP's settings a lot I would suggest using the hard reset button on the AP (usually a tiny button held in with a pen tip or similar) to return it to factory default values, just to make sure you haven't changed anything that you shouldn't have!
From the default state, you should only need to find the AP's name (which you can get from the gui wifi config utilities, even if they fail to connect!)
There'll be no encryption key at this stage to worry about.
You should at least get a wifi link up at this stage.
Next, if it's a wireless router with built-in modem, go back into its settings and configure the modem settings only.

If you could give more specific details, maybe post the make/model ap/router you have there maybe we could help a bit more.
Do you have a wifi router/modem/ap box? Is it working fine (internet, etc) over an ethernet link and it's *just* the wireless link you're having trouble with?

Don't  forget to try the manual setup above first, because it *might* just be the wifi gui apps failing!

Good luck.

---

