---
title: "sharing internet thru wifi"
date: 2011-10-18
forum: General Help
---

### Post by amir17901m on 2011-10-18
hey everyone 

i almost like read all of the web pages about this topic ! and non of them led me to a solution !!

i wonder how to share internet with another computer or my android phone (not using ad-hoc) via wireless !!!

and it goes like this :

internet -->etho --> wireless --> other computers or android phones

all the contents of the webpages that i'v read were about sharing internet like these :
internet --> wireless-->eth0-->linux or windows or mac etc.

by the way you guys Rock !!:guitar:

---

### Post by spiky001 on 2011-10-18
Have you tried open network manager edit connections select wireless tab  select your wireless then in the ip4v tab select Method shared with other computors

---

### Post by dave01945 on 2011-10-18
you will need to put the wifi card in master mode using this command

```
sudo ifconfig wlan0 down
sudo iwconfig wlan0 mode master
sudo ifconfig wlan0 up
```

i've presumed wlan0 is your wireless card if not change it appropriately.

also not all wireless devices support master mode so if the above command fails i think your out of luck, ad-hoc is your only option

---

### Post by amir17901m on 2011-10-18
are u sure dave ? because... maybe you don't like it (and i don't like it ) ! but i can do such thing on windows using connectify !!

so i think there's got to be a way !

---

### Post by amir17901m on 2011-10-18
and thanks sparky i'v tried that ! but it doesn't seem to work !

---

### Post by dave01945 on 2011-10-18
I think it is more of a driver issue rather than a hardware issue windows has the advantage of having the manufacturers make drivers for them linux does not. if the commands i gave, gives you an error message saying set failed invalid argument then the driver you have does not support it all you can do then is see if their is another driver or try to write your own the first option is probably easier.

what wireless card do you have they might help

--EDIT--

These pages may be of use they are about using master mode on your wifi card try [**this first**](https://help.ubuntu.com/community/WifiDocs/MasterMode) if not try [**this**](http://linuxwireless.org/en/users/Documentation/hostapd)

---

### Post by amir17901m on 2011-10-18
i tried to put my wlan0 to master mode but it seems to fail

this is the error :

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.

---

### Post by amir17901m on 2011-10-18
i tried to put my wlan0 to master mode but it seems to fail

this is the error :

Error for wireless request "Set Mode" (8B06) :
    SET failed on device wlan0 ; Invalid argument.
:(

---

### Post by amir17901m on 2011-10-18
ok thanks !!! i will try ;)

---

### Post by dave01945 on 2011-10-18
I Edited my last post try them sites i provided

---

### Post by amir17901m on 2011-10-18
in the iw list on Supported interface modes AP is listed , so i should be able to use my card as an AP but i can't ! and the article says if it's listed just enable restricted drivers ! but i can't do that in 11.04 natty ! 
can you help me on this ?

---

### Post by dave01945 on 2011-10-19
What wireless card do you have i'll see if i can find out what to do

---

### Post by amir17901m on 2011-10-19
it's a Atheros AR9285 on a asus n82jq laptop !!! thanks again lad !!

---

### Post by dave01945 on 2011-10-19
by the looks of it [this](http://linuxwireless.org/en/users/Documentation/hostapd) is the guide you need for that wireless card (i have the same one) i tried the version that is in synaptic it seems to work fine so get that and try to follow the config options on the site I didn't do the whole setup myself because i currently have no need for it but i did the testing part and it didn't give the errors they speak of give it a go and let us know how it goes

[this](https://help.ubuntu.com/community/SharingMobileBroadband#hostapd) may also be of use not sure if you are using mobile broadband but it explains a bit about the config file and the iptables setup

---

### Post by amir17901m on 2011-10-21
when i want to compile hostapd i get 1 error and the article says if you get these kind of errors just install libnl-1 or later !!! i'm using ubuntu 11.10 ! i checked in synaptic package manager and libnl-2 libnl-3 are preinstalled !! 
i really don't know what to do and this problem is killing me :(

i know for sure that my wireless card supports AP !!!

that's because when i run ```
iw
``` list it lists :

	Supported interface modes:
		 * IBSS
		 * managed
		**_ * AP_**
		 * AP/VLAN
		 * WDS
		 * monitor
		 * mesh point
		 * Unknown mode (8)
		 * Unknown mode (9)
	Supported commands:
		 * new_interface
		 * set_interface
		 * new_key
		 * new_beacon
		 * new_station
		 * new_mpath
		 * set_mesh_params
		 * set_bss
		 * authenticate
		 * associate
		 * deauthenticate
		 * disassociate
		 * join_ibss
		 * Unknown command (68)
		 * Unknown command (55)
		 * Unknown command (57)
		 * Unknown command (59)
		 * Unknown command (67)
		 * set_wiphy_netns
		 * Unknown command (65)
		 * Unknown command (66)
		 * connect
		 * disconnect

and [here]("https://help.ubuntu.com/community/WifiDocs/MasterMode") it says that you just need to enable restricted drivers to run an AP !!! i don't knowww how to do that ! and when i look for additional drivers there's no such option to enable restricted drivers :(

---

### Post by dave01945 on 2011-10-21
have you tried to install hostapd from synaptic i'm on 11.04 and it's in their for me would have thought it was still in their for 11.10 

also although it is a atheros card it's not using the atheros(madwifi) it's using the mac80211 atleast mine is and it is the same card

use this to find out

```
lsmod | grep ath9k
```

---

### Post by amir17901m on 2011-10-21
i installed hostapd from synaptic and i ran lsmod | grep ath9k and it returned 
> ath9k                 127538  0 
mac80211              310872  1 ath9k
ath9k_common           13839  1 ath9k
ath9k_hw              312866  2 ath9k,ath9k_common
ath                    24067  2 ath9k,ath9k_hw
cfg80211              199587  3 ath9k,mac80211,ath

what do you suggest ?

---

### Post by dave01945 on 2011-10-21
try [this](http://linuxwireless.org/en/users/Documentation/hostapd#Establishing_Baseline_for_Configuration) site, it explains how to configure hostapd also [this](https://help.ubuntu.com/community/SharingMobileBroadband#hostapd) and [this](http://ubuntuforums.org/showthread.php?t=1488953) should be helpful have a read through them and if you get stuck let us know and i'll see what i can do.

---

