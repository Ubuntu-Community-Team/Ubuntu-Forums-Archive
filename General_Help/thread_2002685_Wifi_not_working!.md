---
title: "Wifi not working!"
date: 2012-06-13
forum: General Help
---

### Post by LionsFootball on 2012-06-13
Hello, my wifi is not working but when I connect to the router trough the Ethernet cord it works. It is only since I upgraded to the 12.04 since this has happened. Any suggestions?

---

### Post by idoitprone on 2012-06-13
> **LionsFootball said:**
> Hello, my wifi is not working but when I connect to the router trough the Ethernet cord it works. It is only since I upgraded to the 12.04 since this has happened. Any suggestions?


```
lspci  -nnk
```

---

### Post by Kira_Belka on 2012-06-13
Post result of > lspci 
Also mb you describe your hardware? it's a bit hard to quess it on the distance (my magic wand tells nothing about your PC :lolflag: )

---

### Post by LionsFootball on 2012-06-13
It is a Gateway NV79. I will post the link with the info. I'm not 100% sure what you need to know.

[http://support.gateway.com/s/notebook/2009/gateway/nv/NV79/NV79sp2.shtml]("http://support.gateway.com/s/notebook/2009/gateway/nv/NV79/NV79sp2.shtml")

Let me know if there is any other info you need. 

Thank you!

---

### Post by LionsFootball on 2012-06-13
> **idoitprone said:**
> ```
lspci  -nnk
```

I am very new to ubuntu. I am loving the system but please excuse me being so new with some of these questions! I put in the code so what should I look for and/or do next?

Thanks for your time!

---

### Post by wildmanne39 on 2012-06-14
Hi, welcome to the forum! Please open a terminal ctrl+alt+t copy and paste the following commands into it one line at a time, then paste the results here:

```
cat /etc/lsb-release; uname -a
lspci -nnk | grep -iA2 net
lsusb
iwconfig
rfkill list all
lsmod
```
here by clicking on new reply and click # and paste the information between the brackets.
Thank you

---

### Post by Kira_Belka on 2012-06-14
Application menu - accessories - terminal

then type lspci 
copy result
here.
so same for lsusb 
:)

---

### Post by LionsFootball on 2012-06-14
bigbertha@ubuntu:~$ cat /etc/lsb-release; uname -a
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04 LTS"
Linux ubuntu 3.2.0-23-generic #36-Ubuntu SMP Tue Apr 10 20:39:51 UTC 2012 x86_64 x86_64 x86_64 GNU/Linux
bigbertha@ubuntu:~$ lspci -nnk | grep -iA2 net
01:00.0 Ethernet controller [0200]: Broadcom Corporation NetLink BCM57780 Gigabit Ethernet PCIe [14e4:1692] (rev 01)
	Subsystem: Acer Incorporated [ALI] Device [1025:0139]
	Kernel driver in use: tg3
--
02:00.0 Network controller [0280]: Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) [168c:002a] (rev 01)
	Subsystem: Foxconn International, Inc. T77H047.31 802.11bgn Wireless Half-size Mini PCIe Card [AR9283] [105b:e01f]
	Kernel driver in use: ath9k
bigbertha@ubuntu:~$ lsusb
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 002 Device 002: ID 8087:0020 Intel Corp. Integrated Rate Matching Hub
Bus 001 Device 003: ID 064e:a103 Suyin Corp. Acer/HP Integrated Webcam [CN0314]
Bus 002 Device 003: ID 05ac:129c Apple, Inc. 
bigbertha@ubuntu:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:"rck"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: 00:17:3F:58:93:C8   
          Bit Rate=54 Mb/s   Tx-Power=16 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=45/70  Signal level=-65 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:206   Missed beacon:0

eth0      no wireless extensions.

bigbertha@ubuntu:~$ rfkill list all
0: acer-wireless: Wireless LAN
	Soft blocked: no
	Hard blocked: no
1: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: no
bigbertha@ubuntu:~$ lsmod^C
bigbertha@ubuntu:~$

---

### Post by wildmanne39 on 2012-06-14
Hi, run this code one line at a time in the terminal and see if it come on, do not reboot we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

```
Thanks

---

### Post by LionsFootball on 2012-06-14
This did work. I had internet but it was very slow at home. After all of this it is working great now! Here is the results..

bigbertha@ubuntu:~$ sudo ifconfig wlan0 down
[sudo] password for bigbertha: 
bigbertha@ubuntu:~$ sudo rmmod -f ath9k
bigbertha@ubuntu:~$ sudo modprobe ath9k nohwcrypt=1
WARNING: All config files need .conf: /etc/modprobe.d/Untitled Document 1, it will be ignored in a future release.
bigbertha@ubuntu:~$ sudo ifconfig wlan0 up
bigbertha@ubuntu:~$ 

Thank you!


> **wildmanne39 said:**
> Hi, run this code one line at a time in the terminal and see if it come on, do not reboot we will need to make it permanent.
```
sudo ifconfig wlan0 down
sudo rmmod -f ath9k
sudo modprobe ath9k nohwcrypt=1
sudo ifconfig wlan0 up

```
Thanks

---

### Post by wildmanne39 on 2012-06-14
Hi, okay we need to make it permanent:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
please use thread tools at the top of the page to mark the thread solved.
Thanks

---

### Post by LionsFootball on 2012-06-14
> **wildmanne39 said:**
> Hi, okay we need to make it permanent:
```
echo "options ath9k nohwcrypt=1" | sudo tee /etc/modprobe.d/ath9k.conf
sudo modprobe -rfv ath9k
sudo modprobe -v ath9k
```
please use thread tools at the top of the page to mark the thread solved.
Thanks

Do I put them in one at a time or all together? Also, do I need to restart my laptop afterwords?

Thanks for all your help!!!

---

### Post by wildmanne39 on 2012-06-14
Hi, one at a time and yes reboot.
Thanks

---

### Post by LionsFootball on 2012-06-14
> **wildmanne39 said:**
> Hi, one at a time and yes reboot.
Thanks

Thank you again! I restart the laptop and it's running great! I really like the Ubuntu 12.04 and was afraid and wouldn't work. I am a realtor and have been looking a Ipads but I'm liking this ubuntu 12.04 and might look into a tablet that runs ubuntu for work use.

---

### Post by wildmanne39 on 2012-06-14
Your welcome!
Enjoy

---

