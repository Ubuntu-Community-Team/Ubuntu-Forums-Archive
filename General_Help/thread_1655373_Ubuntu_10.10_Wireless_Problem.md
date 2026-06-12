---
title: "Ubuntu 10.10 Wireless Problem"
date: 2010-12-29
forum: General Help
---

### Post by VonBlood on 2010-12-29
[FONT=Tahoma][SIZE=2] [SIZE=2]Hey guys,[/SIZE]
 [SIZE=2]
 [/SIZE]
 [SIZE=2]I know this question has peen posed thousands of  times already, but I'm at my wits end. I think I've seen pretty much  evey post on this problem already and said what they told me to do, and  still it doesn't help. I am a Ubuntu newb though, so bear with me :)
[/SIZE]
 [SIZE=2]
 [/SIZE]
 [SIZE=2]Anyway, my problem is this; I recently decided I  wanted to run Ubuntu on my new latop, which already has Windows 7 on it.  Everything works just fine, except it seems I can't connect to any  wireless connection, it's just turned off (the light for WiFi on my laptop as wel))[/SIZE]
 [SIZE=2]
 [/SIZE]
 [SIZE=2]Below are some things that may be of help;
The wireless card I use is supposed to be supported; [/SIZE]Atheros AR9285 uses driver ath9k as shown by lspci which should work, and I have this installed (I think).
Using rfkill unblock all doesn't work, it's still hard blocked;
 [/SIZE][/FONT]```
job@ubuntu:~$ rfkill list
0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no
1: phy0: Wireless LAN
    Soft blocked: no
    Hard blocked: yes
job@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
job@ubuntu:~$ sudo modprobe ath9k
job@ubuntu:~$ sudo lsmod ath9k
Usage: lsmod

```[FONT=Tahoma][SIZE=2]
I don't know if there's anything else that could be of help, or any of you guys knows what to do, but you'd be my hero if you could help me :)
Thanks beforehand!

 [/SIZE][/FONT]

---

