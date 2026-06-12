---
title: "Networking DHCP Problems with wlan0 and server and other misc. problems."
date: 2006-01-21
forum: General Help
---

### Post by ap0ll0 on 2006-01-21
First thing thanks for reading my post. I just installed Ubuntu 5.10 on my Compaq Proliant 800 and I have run into a couple issues. I needed to get wireless networking running so I could Interent. I probably should have built NDISwrapper from source, but I was lazy and decided to use the builtin ndiswrapper binary. My wireless card is a cheap one I got from CompUSA, I think its a realtek chipset (The driver that came with the cd is Net8185.inf). I got the driver loaded under ndiswrapper, and it says the driver is loaded and the hardware is present. I modprobed it then did a ndiswrapper -m. All went smoothly. I entered my ESSID in iwconfig, that should be it (my router has no wep running) and iwconfig seemed to have found my router. I ran Ifconfig wlan0 up and then went to dhclient3 wlan0 and it couldnt find the dhcp server (it kept trying and eventually said there was no dhcp server 0.o ). This is bizzare because I have 4 computers down here all dual-booting linux and windows and this has never happened before. I have windoze 2000 on the Proliant 800 and it seems to find the dhcp server fine and can access the net. This problem was one of several that happened before when I had Mepis on it but I just figured it was something to do with Mepis. I can not use static IPs on this router since I do not have permission to access the router settings. Any ideas would be appreciated on this one. 

 Second, I am a total n00b with dhcpd. I have no idea what I am doing, but if someone could point me in the way of a good guide or show me how to run it that would be nice. I was going to use dhcpd (on the Proliant) to provide DHCP on my ethernet switch that the proliant 800 is hooked to.

 Third, I don't like using a resolution in X lower than 800 x 600. The Proliant 800 has a 1mb ATI Rage IIC onboard, with a CTX VL700 moniter, and on other distros and windows that have been installed on it can do 800 x 600 or 1024 x 768, but in Ubuntu I can only use 640 x 480. The moniter is not auto detected because I have it hooked up through one Compaq KVM, but I think should be a non-issue. 

 Any advice/help on these is much appreciated

                                  Thanks,
                                    Ap0ll0

---

### Post by ap0ll0 on 2006-01-21
>>bump<<

---

