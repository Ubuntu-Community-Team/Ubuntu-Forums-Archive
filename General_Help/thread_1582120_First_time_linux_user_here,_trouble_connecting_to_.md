---
title: "First time linux user here, trouble connecting to wireless..."
date: 2010-09-26
forum: General Help
---

### Post by rajohns08 on 2010-09-26
Ok so my first time logigng into Ubuntu yesterday i was able to connect to my wireless network, i just had to change a setting to PEAP or something like that. now when i sign in it tells me wireless isn't turned on like it doesnt pick up any networks, its basically acting like my wireless switch is turned off, but its not. any help or troubleshooting suggestions? btw, im completely linux illiterate right now, ive never even seen it before today, just curious as to how it compares to windows.

---

### Post by zealibib slaughter on 2010-09-26
Right click the network manager icon and make sure wireless is enabled.

---

### Post by rajohns08 on 2010-09-26
no thats what im trying to say...its not enabled, but its not allowing me to click enable wireless...

---

### Post by zealibib slaughter on 2010-09-26
try killing network manager in terminal
code
sudo killall NetworkManager

then restart network manager
code
sudo NetworkManager

watch for error messages and post any you see.

---

### Post by rajohns08 on 2010-09-26
> **zealibib slaughter said:**
> try killing network manager in terminal
code
sudo killall NetworkManager

then restart network manager
code
sudo NetworkManager

watch for error messages and post any you see.

after i type that code i get this warning: 

** (NetworkManager:3084): WARNING **: NetworkManager is already running (pid 3081)

ps...and yes i did the killall line first...

---

### Post by spiky001 on 2010-09-26
Hi can you put ```
iwconfig
``` post pouput

---

### Post by rajohns08 on 2010-09-26
adam@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off

---

### Post by spiky001 on 2010-09-26
try  ```
sudo ifconfig wlan0 up
```

---

### Post by rajohns08 on 2010-09-26
nothing happens when i enter that line:

adam@ubuntu:~$ sudo ifconfig wlan0 up
adam@ubuntu:~$

and still same problem

---

### Post by JohnHeikkila on 2010-09-26
Everything happens when you do that. "ifconfig wlan0 up" starts your wireless adapter.

---

### Post by spiky001 on 2010-09-26
ok is this a laptop?

---

### Post by rajohns08 on 2010-09-26
> **spiky001 said:**
> ok is this a laptop?

yes

---

### Post by spiky001 on 2010-09-26
ok there should be a button on it to turn wireless on not sure where is on yours mine is in the front some you have to use Fn+F2 have a look

---

### Post by rajohns08 on 2010-09-26
yeah in my first post i was trying to explain this, but i dont think i said it clearly... my wireless button is turned on already. however, my wireless light is not lit up, which makes me think ubuntu just completely isnt recognizing my wireless hardware at all...

---

### Post by P4man on 2010-09-26
Ive seen ubuntu get confused about the state of the wif kill switch switch when you let the machine run out of battery. 

What machine do you have?

---

### Post by rajohns08 on 2010-09-26
> **P4man said:**
> Ive seen ubuntu get confused about the state of the wif kill switch switch when you let the machine run out of battery. 

What machine do you have?

dell latitude d830. but i havent let machine run out of battery since ive had ubuntu. unless you meant if it has EVER run out of battery...

---

### Post by spiky001 on 2010-09-26
can you connect a eth0 cable and update drivers?

---

### Post by rajohns08 on 2010-09-26
> **spiky001 said:**
> can you connect a eth0 cable and update drivers?

im connected via eth0 right now, but how do i update drivers?

---

### Post by P4man on 2010-09-26
Have a look here, same laptop, same problem and a solution:

[http://ubuntuforums.org/showthread.php?t=1496396](http://ubuntuforums.org/showthread.php?t=1496396)

---

### Post by rajohns08 on 2010-09-26
> **P4man said:**
> Have a look here, same laptop, same problem and a solution:

[http://ubuntuforums.org/showthread.php?t=1496396](http://ubuntuforums.org/showthread.php?t=1496396)

ok that worked, thank you very much. hopefully, when i re-log on it will still work. thanks again.

---

### Post by P4man on 2010-09-26
Lets hope it does. This was a factory installed ubuntu right?
Rather disappointing Dell would ship their laptops with an issue this serious, no matter how easy it is to fix. You may want to contact them about it.

---

### Post by rajohns08 on 2010-09-26
> **P4man said:**
> Lets hope it does. This was a factory installed ubuntu right?
Rather disappointing Dell would ship their laptops with an issue this serious, no matter how easy it is to fix. You may want to contact them about it.

nonono ha sorry didnt clarify. i just installed linux yesterday through wubi. laptop shipped with windows which i still have on system. just testing out linux to see how i like it. one thing ive noticed since i have connected to wireless is that it randomly drops every now and then. ever had that problem before?

---

### Post by spiky001 on 2010-09-26
never used wubi before, I dont know if it works as well as if was installed, have you tried running live cd?

---

### Post by rajohns08 on 2010-09-26
> **spiky001 said:**
> never used wubi before, I dont know if it works as well as if was installed, have you tried running live cd?

no whats live cd?

---

### Post by spiky001 on 2010-09-26
insert cd set machine to boot from cd in bios load cd it will give option to try without changing your system, basically it all runs off the cd not installing anything so you can try it,

---

### Post by P4man on 2010-09-26
Wubi isnt going to cause wifi problems. Using wubi is fine to try it out, but by all means if you decide you want to actually use ubuntu, then do a proper install. Wubi is too fragile, depending on windows file system, you can not expand partition sizes, if you mess up (and you will if you are new to linux) there are only very limited options to restore your system or retrieve your files.

Anyway, back to the dropping wifi. Is your signal strength worse than it is in windows? Poor wifi drivers can do that.  If worst comes to worst, you can actually use windows wifi drivers in ubuntu, but lets first find out what wifi card you have; open a terminal and type

```
lspci

```
and 

```
lsusb

```
copy paste the output here.

---

### Post by rajohns08 on 2010-09-26
```
adam@ubuntu:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PM965/GM965/GL960 PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Quadro NVS 140M (rev a1)
03:01.0 CardBus bridge: O2 Micro, Inc. Cardbus bridge (rev 21)
03:01.4 FireWire (IEEE 1394): O2 Micro, Inc. Firewire (IEEE 1394) (rev 02)
09:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5755M Gigabit Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 4965 AG or AGN [Kedron] Network Connection (rev 61)
adam@ubuntu:~$ 
 
```

```
adam@ubuntu:~$ lsusb
Bus 007 Device 003: ID 0b97:7772 O2 Micro, Inc. OZ776 CCID Smartcard Reader
Bus 007 Device 002: ID 0b97:7761 O2 Micro, Inc. Oz776 1.1 Hub
Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 002: ID 046d:c016 Logitech, Inc. M-UV69a/HP M-UV96 Optical Wheel Mouse
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
adam@ubuntu:~$ 
 
```

---

### Post by P4man on 2010-09-27
You have an intel PRO/Wireless 4965 AG(N). Thats a fairly common card, I wouldnt expect there to be a driver issue, though I cant say for sure.

Id try this first, go to ubuntu software center and install "wicd". That will remove the default network manager. Reboot. You may have to configure your connections again in wicd, but Ive had issues with networkmanager and never any with wicd. Give it a try and let us know.

---

### Post by rajohns08 on 2010-09-30
> **P4man said:**
> You have an intel PRO/Wireless 4965 AG(N). Thats a fairly common card, I wouldnt expect there to be a driver issue, though I cant say for sure.

Id try this first, go to ubuntu software center and install "wicd". That will remove the default network manager. Reboot. You may have to configure your connections again in wicd, but Ive had issues with networkmanager and never any with wicd. Give it a try and let us know.

one thing I've noticed is that my wifi light on my computer blinks randomly on linux but it is always solid on windows. any hints as to the meaning of that? i'm installing wicd now ill let you know how it goes.

---

### Post by rajohns08 on 2010-09-30
> **P4man said:**
> You have an intel PRO/Wireless 4965 AG(N). Thats a fairly common card, I wouldnt expect there to be a driver issue, though I cant say for sure.

Id try this first, go to ubuntu software center and install "wicd". That will remove the default network manager. Reboot. You may have to configure your connections again in wicd, but Ive had issues with networkmanager and never any with wicd. Give it a try and let us know.

ok so i installed wicd but i can't connect to any of the possible types of connections because it keeps telling me my password is wrong. with the stock network manager, i use a (PEAP) connection.

EDIT: just realized if i connect through the normal manager, it seems that it automatically connects me to the wicd connection, however it stays at around 37% signal strength so i'm assuming my problem is a weak signal. it is still dropping every 5 minutes and seems to have gotten a little worse actually.

---

### Post by P4man on 2010-09-30
> **rajohns08 said:**
> one thing I've noticed is that my wifi light on my computer blinks randomly on linux but it is always solid on windows. any hints as to the meaning of that? 

I dont think it means anything. Its the driver making the led blink on activity or keeping it solid when its on.

> ok so i installed wicd but i can't connect to any of the possible types of connections because it keeps telling me my password is wrong. with the stock network manager, i use a (PEAP) connection.

Wicd supports peap as far as I know. Which password is it asking, your peap or your keyring password? If its the keyring (which stores all your passwords), then that is by default the same password as your ubuntu login password. Or it may be empty (no password).
> 
just realized if i connect through the normal manager, it seems that it automatically connects me to the wicd connection, however it stays at around 37% signal strength so i'm assuming my problem is a weak signal. it is still dropping every 5 minutes and seems to have gotten a little worse actually. 

You can try changing the wifi channel on the access point to get a better reception. But if you think it was better in windows, its still possible the drivers arent quite up to snatch. You could try the windows drivers. Install the app 'wireless windows drivers' in software center. THen in system > administration > windows drivers" you can install the windows drivers (point it to the folder containing the .inf files, so not an exe or zip). If you have ubuntu 64 bit you also need the 64 bit windows drivers.

---

### Post by rajohns08 on 2010-09-30
> **P4man said:**
> 
 
 
You can try changing the wifi channel on the access point to get a better reception. But if you think it was better in windows, its still possible the drivers arent quite up to snatch. You could try the windows drivers. Install the app 'wireless windows drivers' in software center. THen in system > administration > windows drivers" you can install the windows drivers (point it to the folder containing the .inf files, so not an exe or zip). If you have ubuntu 64 bit you also need the 64 bit windows drivers.
 
 
ok so i uninstalled NetworkManager, expecting to just reinstall it again to see if that helps, but i can't reinstall it because it says no internet connection found. what do i do now? i tried
 
```

sudo apt-get install NetworkManager
```
 
but it could not find the file.

---

### Post by 98cwitr on 2010-09-30
try 

```
sudo apt-get install network-manager
```

Or just check the Software Center under Applications.

To connect to a wireless network, single left-click on the network icon and it should show you your wireless networks.

---

### Post by rajohns08 on 2010-09-30
> **98cwitr said:**
> try 
 
```
sudo apt-get install network-manager
```
 
Or just check the Software Center under Applications.
 
To connect to a wireless network, single left-click on the network icon and it should show you your wireless networks.
 
sigh...i uninstalled network manager, so that icon is no longer there. also when i try to install it again from the software center it says i need an internet connection which i dont have.

---

### Post by spiky001 on 2010-09-30
I can see this ending in a reinstall

---

### Post by rajohns08 on 2010-09-30
> **spiky001 said:**
> I can see this ending in a reinstall
 
fair enough. just tell me how i can reinstall 9.10 using wubi. everytime i try to wubi install the only option is 10.04

---

### Post by spiky001 on 2010-09-30
Why mot use 10.04? do you have to wubi instal?

---

### Post by rajohns08 on 2010-09-30
> **spiky001 said:**
> Why mot use 10.04? do you have to wubi instal?
 
because 10.04 is the one ive been having the problem with...and wubi just seems by far the easiest way to install for dual boot with windows.

---

### Post by spiky001 on 2010-09-30
so you must of had the 9.04 disc just reuse it, uninstal the wubi partition then reinstal as before

---

### Post by P4man on 2010-09-30
How, slow down. No need to reinstall. In linux everything is case sensitive.

```
sudo apt-get get install network-manager
```

A dash and no uppercases.
If you didnt purge it, it should still have those files and not need a working internet connection. If that fails, just open a file browser and browse to

/var/cache/apt/archives

If network manager isnt there, then surely wicd still is. Use that to get online.

Worst case, download the deb on a different machine from here:
[http://ch.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/](http://ch.archive.ubuntu.com/ubuntu/pool/main/n/network-manager/)

Copy it to a stick and double click it to install. Make sure you get the right version (AMD64 for 64 bit, i386 for 32 bit). Grab the latest non git one, or go ahead and try the git one, perhaps it even solves your problem.

---

