---
title: "connected to wireless network but no internet"
date: 2010-03-02
forum: General Help
---

### Post by prithvi on 2010-03-02
Hello friends,
I have a compaq cq40-133tu laptop. I have windows vista ultimate and ubuntu 9.10 parallely installed. Most of the time i use Ubuntu for programming purpose. But for internet connection i have to go to windows. This is because ubuntu is getting connected to the network but is unable to access internet, whereas the windows can.
I want to totally abandon windows. 
Recently i got internet connection in ubuntu for just 15 minutes or so when i ticked the option AVAILABLE TO ALL USERS. but after that the same story continues and iam not able to access internet.
Details about Internet connection:
This is not my connection, these signals come from nearby building. Its a wifi open public network. 
Please help me to totally abandon windows.
Thanks in advance.

---

### Post by labinnsw on 2010-03-09
[If you are currently using Network Manager, give Wicd a try instead]("http://wicd.sourceforge.net/download.php")

---

### Post by prithvi on 2010-03-09
No brother,it is still not working. Though the interface is much better than Network manager, but still the same problem continues.

---

### Post by dannyboy79 on 2010-03-09
you need to post more details. are you getting a valid ip address from this public wifi spot? what is the signal strength? try iwlist to see signal strength.

[http://en.wikipedia.org/wiki/Wireless_tools_for_Linux#iwlist](http://en.wikipedia.org/wiki/Wireless_tools_for_Linux#iwlist)

---

### Post by prithvi on 2010-03-16
Signal strength fluctuates between 60 and 100 percent.
Ip address is dynamic. Every time i boot up, there is different ip address.
what the point is, when iam getting internet in windows, then why shouldnt i get it in linux.
I have installed wicd, but it is of no use.
please help me with other alternatives.

---

### Post by dannyboy79 on 2010-03-16
please post more info as already requested and we can possibly help you. please post info about wireless card using lspci, lshw, adn other command for trouble shooting wifi. google has all info you need. awaiting response that has valuable information.

---

### Post by ushills on 2010-03-16
Can you ping the address of your router

```
ping 192.168.1.1
``` or something like that, then try an external host, i.e opendns with

```
ping 208.67.220.220
```

If this is the case then please post the output of 

```
cat /etc/resolv.conf
```
```
sudo iwconfig
```
and 
```
sudo ifconfig
```

---

### Post by ushills on 2010-03-16
also post the wireless card details, with 

```
sudo lspci
``` if it is a PCI card

or

```
sudo lsusb
```if it is USB.

Karmic pre-update had an issue with wireless cards disconnecting, specifically RT62/RT2561.

---

### Post by 3rdalbum on 2010-03-16
Try changing your DNS addresses to point to OpenDNS (208.67.222.222,208.67.220.220). I don't use Wicd so I can't advise how to do it in that.

---

### Post by matzen on 2010-03-16
I had the exact same problem. Searched far and wide on Google for weeks before I found a solution. In the end I installed MadWiFi drivers which helped (mainly for Atheros cards). You can follow the procedure here: [http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

It did the trick. Never had a network issue since.

---

### Post by prithvi on 2010-04-11
sorry for not replying. I was on a long tour to kashmir. I will be trying matzens solution and also details of the system,.

---

### Post by prithvi on 2010-04-11
hey matzen. The drivers you insisted are for edgy and for feisty. Im currently using karmic. Is it necessary because edgy and feisty are too old os which may require some tweak ins but mine is somewhat updated regularly.

---

### Post by prithvi on 2010-05-19
Its an auto dhcp connection.

---

