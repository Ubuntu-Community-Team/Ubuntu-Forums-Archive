---
title: "Going crazy = wpaSupplicant + NdisWrapper + AES + Acer 4400"
date: 2006-04-07
forum: General Help
---

### Post by MrMojoRising on 2006-04-07
I hoped it wouldn't come down to this but it has......i've done all i can on my own....i need your help!
If i had known what a pain it was to set up WPA encryption using a wireless connection in linux i'd probably never want to be born. anyway.......


I have an Acer TravelMate 4404wlmi notebook with a ...
```
0000:06:05.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```
...miniPCI card built in. I spent the better part of yesterday just messing with setting up acer_acpi and ndiswrapper to get the wireless working somewhat. However in order to succesfully do this i had to disable all security on my Router (belkin 54g pre-n if you're intrested) to do it. I was able to get a full connection after following all of the guides and HowTo's on these forums.



Then i decided to shoot myself in the face and try to get my encryption back on. (Big mistake)




I figured everything should be okay seeing as i got this far....so i followed [this guide]("http://ubuntuforums.org/showthread.php?t=90450") and changed the file to allow for AES (CCMP)....mine now looks like this.
```
# Minimal /etc/wpa_supplicant.conf to associate with open
#  access points. Please see 
#  /usr/share/doc/wpasupplicant/wpa_supplicant.conf.gz for more complete
#  configuration parameters.

ctrl_interface=/var/run/wpa_supplicant
ctrl_interface_group=0

eapol_version=1
ap_scan=2
fast_reauth=1


# reading passphrase from stdin
network={
	ssid="myessid"
	scan_ssid=1
	mode=0
	proto=RSN
	pairwise=CCMP
	group=CCMP
	key_mgmt=WPA-PSK
	psk=ba8................................cc1f
}
```


Unfortunatley this doesn't work.......
I now get this ugly error message when i try to manually start wpa_supplicant...

```

@Enoch:~$ sudo wpa_supplicant -i wlan0 -D ndiswrapper -c /etc/wpa_supplicant .conf -w -d
Initializing interface 'wlan0' conf '/etc/wpa_supplicant.conf' driver 'ndiswrapp er'
Configuration file '/etc/wpa_supplicant.conf' -> '/etc/wpa_supplicant.conf'
Reading configuration file '/etc/wpa_supplicant.conf'
ctrl_interface='/var/run/wpa_supplicant'
eapol_version=1
ap_scan=2
fast_reauth=1
Priority group 0
   id=0 ssid='pandora'
Initializing interface (2) 'wlan0'
EAPOL: SUPP_PAE entering state DISCONNECTED
EAPOL: KEY_RX entering state NO_KEY_RECEIVE
EAPOL: SUPP_BE entering state INITIALIZE
EAP: EAP entering state DISABLED
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
ioctl[SIOCSIWPMKSA]: No such device
SIOCGIWRANGE: too old (short) data - assuming WPA is not supported
Own MAC address: 00:16:ce:13:2c:2b
wpa_driver_wext_set_key: alg=0 key_idx=0 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=1 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=2 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
wpa_driver_wext_set_key: alg=0 key_idx=3 set_tx=0 seq_len=0 key_len=0
ioctl[SIOCSIWENCODEEXT]: No such device
Driver did not support SIOCSIWENCODEEXT, trying SIOCSIWENCODE
Setting scan request: 0 sec 100000 usec
Using existing control interface directory.
Wireless event: cmd=0x8b06 len=12
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
RTM_NEWLINK, IFLA_IFNAME: Interface 'wlan0' added
Wireless event: cmd=0x8b2a len=24
Wireless event: cmd=0x8b2a len=24
Wireless event: cmd=0x8b2a len=24
Wireless event: cmd=0x8b2a len=24
State: DISCONNECTED -> SCANNING
Trying to associate with SSID 'pandora'
Cancelling scan request
WPA: clearing own WPA/RSN IE
Automatic auth_alg selection: 0x1
WPA: Failed to parse WPA IE from association info
WPA: Set cipher suites based on configuration
WPA: Selected cipher suites: group 16 pairwise 16 key_mgmt 2
WPA: clearing AP WPA IE
WPA: clearing AP RSN IE
WPA: using GTK CCMP
WPA: using PTK CCMP
WPA: using KEY_MGMT WPA-PSK
WPA: Set own WPA IE default - hexdump(len=22): 30 14 01 00 00 0f ac 04 01 00 00 0f ac 04 01 00 00 0f ac 02 00 00
No keys have been configured - skip key clearing
State: SCANNING -> ASSOCIATING
Setting authentication timeout: 5 sec 0 usec
EAPOL: External notification - EAP success=0
EAPOL: External notification - EAP fail=0
EAPOL: External notification - portControl=Auto
State: ASSOCIATING -> DISCONNECTED
No keys have been configured - skip key clearing
EAPOL: External notification - portEnabled=0
EAPOL: External notification - portValid=0
No keys have been configured - skip key clearing
```


I'm at a loss for ideas:-k ...... my head hurts](*,) ....if anyone can help me out it'd be greatly appreciated8) .

---

### Post by Ramses de Norre on 2006-04-07
```
No keys have been configured - skip key clearing
ioctl[SIOCSIWPMKSA]: No such device
```
Those lines don't look good. 

Why can't you use WEP instead of WPA? I know it's a little less secure but very easy to configure (just give in the code) and in combination with MAC control (which only needs to be enabled on the router) your network will be pretty safe.

---

### Post by MrMojoRising on 2006-04-07
I could use WEP but that's not the point. It's mostly the principal. Plus i have alot of friends come over to use my wireless and configuring their MACs in the router (albeit simple yet timeconsuming) is just not my idea of a good time.

Have you/has anyone seen that particular error message before?
I tried googling the error but didn't get any good hits.



Also could this have anything to do with the fact that i'm using an AMD64 and have the 64bit Ubuntu?

---

### Post by firecat53 on 2006-04-08
I don't have your particular card, but I use this setup with ndiswrapper and another broadcom minipci card for vanilla wpa-psk:

/etc/wpa_supplicant.conf:
```
network={
   ssid="networkname"
   #psk="mypassphrase"
   psk=34150987asdfasdfjkh3407etcetcetc
   key_mgmt=WPA-PSK
   proto=WPA
}
```

and then start wpa_supplicant (for testing....once it works you can integrate it into /etc/network/interfaces) with:
```
sudo wpa_supplicant -w -D ndiswrapper -c /etc/wpa_supplicant.conf -i wlan0 -dd
```.

Another thing to try is compiling wpa_supplicant and ndiswrapper from source. The more recent versions have fixed issues with certain drivers and cards and incompatibilities with wpa. I've typically used compiled versions of ndiswrapper and wpa_supplicant with the best results. Also, try adding or deleting some of the wpa_supplicant.conf parameters (e.g. ap_scan, mode, fast_reauth, etc) one at a time to see if it changes anything. My conf file is I think about the minimum amount of info needed for wpa to function. You may need more!

Good luck!

Scott

---

### Post by MrMojoRising on 2006-04-08
Thanks Scott, 
okay I'll give that a shot once i get back home and let you know how it goes....

Also will that procedure allow for AES (ccmp) encryption.....or this this only for TKIP or does it not even matter.

---

### Post by MrMojoRising on 2006-04-10
Okay that didn't work. I think the wpa_supplicant.conf file needs to be changed a little differntly to use AES. 

Guess what......while working this issue out [THIS]("http://ubuntuforums.org/showthread.php?t=157892") happened. So needless to say this problem has been put on hold untill [THIS]("http://ubuntuforums.org/showthread.php?t=157892") issue has been resolved.


Starting to think that maybe Acer was a bad choice for a new laptop:(

---

### Post by wtw1ster on 2006-06-24
[QUOTE=Ramses de Norre]```
No keys have been configured - skip key clearing
ioctl[SIOCSIWPMKSA]: No such device
```
Those lines don't look good. 

Why can't you use WEP instead of WPA? I know it's a little less secure but very easy to configure (just give in the code) and in combination with MAC control (which only needs to be enabled on the router) your network will be pretty safe.[/QUOTE]

WEP encryption can easily be cracked in under 3 minutes now days.  I fully recommend using WPA!    ;)

---

