---
title: "Broadcam wireless still having issues, plz help i dnt wanna go back to vista :("
date: 2010-02-09
forum: General Help
---

### Post by actsofaith on 2010-02-09
Hi
  After days of research, I managed to finally get my broadcom sta wireless 'active and ready to use', yet i still cant seem to log on to the internet. Their is  blue light on for the wireless indicating its on, and i am picking up wireless signals, but when i try to log on to my network it says "wireless disconnected" every time. Im kinda stuck at this point, so here i am asking for your help, any leads will be appreciated. 
Please keep your answers noob friendly!
thanks in advance

---

### Post by bobcollard on 2010-02-09
> **actsofaith said:**
> Hi
  After days of research, I managed to finally get my broadcom sta wireless 'active and ready to use', yet i still cant seem to log on to the internet. Their is  blue light on for the wireless indicating its on, and i am picking up wireless signals, but when i try to log on to my network it says "wireless disconnected" every time. Im kinda stuck at this point, so here i am asking for your help, any leads will be appreciated. 
Please keep your answers noob friendly!
thanks in advance
Have you entered your ISP information in "Edit Connections" by right clicking on the icon in the taskbar?  If so, it may be a matter of using Automatic (DHCP) or using Automatic (DHCP) with Addresses in the IPv4.  There also may be a switch or button on your keyboard for use in airplanes that is turned off.

---

### Post by actsofaith on 2010-02-09
> **bobcollard said:**
> Have you entered your ISP information in "Edit Connections" by right clicking on the icon in the taskbar? If so, it may be a matter of using Automatic (DHCP) or using Automatic (DHCP) with Addresses in the IPv4. There also may be a switch or button on your keyboard for use in airplanes that is turned off.
  thanks for replying, i have by default an eth1 connection , i also set one up for my wireless network via this site >> [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) , then i applied the 'auto with addresses' for one of them then both connections jus because i wasnt sure which one u were talking about, thing is neither of them worked ....

---

### Post by bobcollard on 2010-02-09
> **actsofaith said:**
> thanks for replying, i have by default an eth1 connection , i also set one up for my wireless network via this site >> [https://help.ubuntu.com/community/NetworkManager0.7](https://help.ubuntu.com/community/NetworkManager0.7) , then i applied the 'auto with addresses' for one of them then both connections jus because i wasnt sure which one u were talking about, thing is neither of them worked ....
As I tried to point out it can be an Either/Or situation.  Try it with just Automatic.  If you set up two addresses you have to determine one of them as default.  Also check all of your numbers in DHCP.  I once hit the (=) instead of the (-) and screwed that up.  It is very unforgiving.

---

### Post by actsofaith on 2010-02-09
> **bobcollard said:**
> As I tried to point out it can be an Either/Or situation. Try it with just Automatic. If you set up two addresses you have to determine one of them as default. Also check all of your numbers in DHCP. I once hit the (=) instead of the (-) and screwed that up. It is very unforgiving.
  
bob , i did it both ways then i tried to connect ,that itself took cpl minutes only to let me know that 'wireless is disconnected", could it be in how i set up the connection, please let me know if this sounds correct 
 for ssid - my network name 
mode- infrastructure (50/50 chance with this one)
BSSID - from what ive been reading this i can skip
Mac address: my mac address 
MTU -automatic 
theres no wireless security 
and IPV4 - 1st try auto 
              - 2nd  auto with addresses
ipv6- left that alone, maybe i shouldnt have??

---

### Post by efflandt on 2010-02-09
Although, the Broadcom device shows up in ifconfig as an eth# device, it is not really and Ubuntu Network Connections knows it.  In Network Connections > Wired for Auto eth0 try **UN**checking "Connect automatically".  Then under Wireless enter your SSID, check that to Connect automatically, set Wireless Security, and anything not automatic in IPv4 Settings.  Although, for some reason you might need to edit the wireless settings for that connection again to make everything stick.

That has always worked for me whether Broadcom STA with BCM4311 or BCM4312, or Broadcom B43 with BCM4328.  In fact when I initially configured wireless for a recognized USB wireless device, activated Broadcom STA, then rebooted without the USB wireless, it recognized and automatically used built-in BCM4312 wireless.

Note that if you want wireless to work from USB Startup Disk Creator (iso on bootable USB) with persistent data, once you activate Broadcom STA and reboot, you need to **sudo modprobe wl** (small WL) for it to work.  But you should not have to do that for a regular installed system.

---

### Post by bobcollard on 2010-02-09
> **actsofaith said:**
> bob , i did it both ways then i tried to connect ,that itself took cpl minutes only to let me know that 'wireless is disconnected", could it be in how i set up the connection, please let me know if this sounds correct 
 for ssid - my network name 
mode- infrastructure (50/50 chance with this one)
BSSID - from what ive been reading this i can skip
Mac address: my mac address 
MTU -automatic 
theres no wireless security 
and IPV4 - 1st try auto 
              - 2nd  auto with addresses
ipv6- left that alone, maybe i shouldnt have??
Don't forget to check the box for "Available to all users" and I left my Mac Address blank.  IPv6 I leave alone too.

---

### Post by actsofaith on 2010-02-09
> **efflandt said:**
> Although, the Broadcom device shows up in ifconfig as an eth# device, it is not really and Ubuntu Network Connections knows it. In Network Connections > Wired for Auto eth0 try **UN**checking "Connect automatically". Then under Wireless enter your SSID, check that to Connect automatically, set Wireless Security, and anything not automatic in IPv4 Settings. Although, for some reason you might need to edit the wireless settings for that connection again to make everything stick.
 
That has always worked for me whether Broadcom STA with BCM4311 or BCM4312, or Broadcom B43 with BCM4328. In fact when I initially configured wireless for a recognized USB wireless device, activated Broadcom STA, then rebooted without the USB wireless, it recognized and automatically used built-in BCM4312 wireless.
 
Note that if you want wireless to work from USB Startup Disk Creator (iso on bootable USB) with persistent data, once you activate Broadcom STA and reboot, you need to **sudo modprobe wl** (small WL) for it to work. But you should not have to do that for a regular installed system.
 its nice when things jus 'work', this is so frustrating  i wouldnt mind a "diagnose and repair function" right about noww or anything user-friendly,
ok i did what u jus said  but im a little confused on what i should put under IPV4 settings 
for DNS server ( mine or the networks?)
Searhc domains ? and where can i find the DHCP client ID

---

### Post by bobcollard on 2010-02-09
> **actsofaith said:**
> its nice when things jus 'work', this is so frustrating  i wouldnt mind a "diagnose and repair function" right about noww or anything user-friendly,
ok i did what u jus said  but im a little confused on what i should put under IPV4 settings 
for DNS server ( mine or the networks?)
Searhc domains ? and where can i find the DHCP client ID
Sounds like time to call out the big guns. (Your Internet Service Provider.)  Mine is ATT and they walked me through it.  Write everything down because you will need it again the next time.  Search Domain is "gnome.org"  Lower case without the quotes.  Sorry, I can't help with the numbers because they are different for each ISP.

---

### Post by actsofaith on 2010-02-09
> **bobcollard said:**
> Sounds like time to call out the big guns. (Your Internet Service Provider.) Mine is ATT and they walked me through it. Write everything down because you will need it again the next time. Search Domain is "gnome.org" Lower case without the quotes. Sorry, I can't help with the numbers because they are different for each ISP.
 ill do that in a minute,im on my wireless info site for linksy  all i need to know is the general format dns server is it like two ip address ( sry for comp illiteracy) and what is the DHCP client id is that also an address

---

### Post by bobcollard on 2010-02-09
> **actsofaith said:**
> ill do that in a minute,im on my wireless info site for linksy  all i need to know is the general format dns server is it like two ip address ( sry for comp illiteracy) and what is the DHCP client id is that also an address
DHCP is a series of numbers.  Mine starts with 00-01-00-01-11-95-E9 XXXXXX  sorry can't include it all.  It's Hexidecimal, hence the letters.  DNS will be something like 192.168.1.100 Again using random numbers at the end.  With these numbers people can find your router and get control of your computer.  I'm using Linksys G myself for a router.

---

### Post by wojox on 2010-02-09
What does :

```
lspci | grep Broadcom
```

Tell you?

---

### Post by actsofaith on 2010-02-09
> **wojox said:**
> What does :
 
```
lspci | grep Broadcom
```
 
Tell you?
 2:00 Network controller: Broadcome BCM4312 802.11

---

### Post by actsofaith on 2010-02-09
> **bobcollard said:**
> DHCP is a series of numbers. Mine starts with 00-01-00-01-11-95-E9 XXXXXX sorry can't include it all. It's Hexidecimal, hence the letters. DNS will be something like 192.168.1.100 Again using random numbers at the end. With these numbers people can find your router and get control of your computer. I'm using Linksys G myself for a router.
 this is more work than i thought, is it necessary for me to add an automatic connection , if not is there an alternative way, mayb some program i could download

---

### Post by wojox on 2010-02-09
I have the same on my laptop. I just downloaded:

```
sudo apt-get install bcmwl-kernel-source
```

Rebooted and entered my key, then all was good.

---

### Post by actsofaith on 2010-02-09
> **wojox said:**
> I have the same on my laptop. I just downloaded:
 
```
sudo apt-get install bcmwl-kernel-source
```
 
Rebooted and entered my key, then all was good.
  
the same exact one? 
looks like i culd be saved =) 
tho i have tried the bcmwl-kernel-source 
is there any more info i can give u so I can know were exctly i messed up ..

---

### Post by bobcollard on 2010-02-09
Try this Thread:

[http://ubuntuforums.org/showthread.php?t=1368699](http://ubuntuforums.org/showthread.php?t=1368699)

---

### Post by efflandt on 2010-02-09
I think you may be trying too hard to make unnecessary settings.  In Network Connections, everything does not need to be filled in.  If your wireless router does DHCP all you really should have to enter  (besides checking connect automatically and all users) is SSID and Wireless Security.  Then it should automatically get IP, netmask, gateway, and nameserver(s) from your wireless router.

Things in Linux tend to be case sensitive.  For example in my case my SSID is 2WIRE106, so 2Wire106 or 2wire106 might not work (I have not really tested that).

---

### Post by actsofaith on 2010-02-10
hey 
I managed to get my wireless to connect to net,then i had some problems loading the websites but oncce i changed the nameserver to the right dns using info from [http://whoooop.co.uk/2009/06/07/ubuntu-wifi-wireless-connected-but-no-internet/](http://whoooop.co.uk/2009/06/07/ubuntu-wifi-wireless-connected-but-no-internet/)
everything started to work fine, 
thanks alot to those who have helped, your great for that:KS

---

### Post by bobcollard on 2010-02-10
> **actsofaith said:**
> hey 
I managed to get my wireless to connect to net,then i had some problems loading the websites but oncce i changed the nameserver to the right dns using info from [http://whoooop.co.uk/2009/06/07/ubuntu-wifi-wireless-connected-but-no-internet/](http://whoooop.co.uk/2009/06/07/ubuntu-wifi-wireless-connected-but-no-internet/)
everything started to work fine, 
thanks alot to those who have helped, your great for that:KS
Wonderful;!  Now that everything is correct, please go to your first post and Edit the Subject line by adding [Solved]  That way people can find the solutions they crave or pass it up/

---

