---
title: "Hardware and kernel upgrade broke system"
date: 2012-09-18
forum: General Help
---

### Post by lsutiger on 2012-09-18
Several months back, I bought a new machine, an Acer 5560-7402. I use this computer for my media server and it runs Win 7. I was curious how fast my current installation of Ubuntu would run (10.04) on the machine, so I pulled my hard drive and installed in the new computer (as this has been flawless for me in the past). Well, this one also ran flawlessly. And, really quick! I was impressed!

So I decide to buy another one in order to upgrade. This time the 5560-7402 was not available. SO I looked at the 5560-7414. The specs posted for the computer were identical. Unfortunately, the chipset of the networking was not posted.

When I plugged in the machine, I had no networking. I downloaded the tg3 driver from broadcom in order get a wired connection. I then went through several tutorials on how to install the driver for my wireless card (also broadcom). After many failures, I decided I was going to install a wireless card brand that is usually friendly with Linux (Atheros - AR928X). At least now the wireless card was detected but not activated.

The last thing I did was install [from here ]("https://help.ubuntu.com/community/WifiDocs/Device/Atheros/AR9285").
Now my video driver will not load (and I can not install - I get errors), my wired connection is no longer available and when I try to install the driver for the wired I receive errors.

Anybody willing to help me with this? I know more information is needed, but I am not sure what information will be needed for the person willing to help.


Thank you in advance!

---

### Post by lsutiger on 2012-09-18
Update: I went into the grub menu and chose a different kernel. Now I have wired connection back up and the video drivers work. Now if I could get wireless working this upgrade would be complete!

---

### Post by einonm on 2012-09-18
Hi, firstly, you'll need to provide the wifi hardware you are using. If you can open a terminal and type 'lsusb' then 'lspci' and post the result, that would be a start.

---

### Post by lsutiger on 2012-09-18
TY! The Model is a Atheros AR928X. From lspci:
Atheros Communications Inc. AR928X Wireless Network Adapter (PCI-Express) (rev 01)

---

### Post by f8l_0e on 2012-09-18
Try editing /etc/udev/rules.d/70-persistent-net.rules (make a backup first)

Comment out the entries for your previous motherboard's nics as they might be conflicting

See if your new wireless card is already in here and set it to wlan0, if it isn't already.

Here is example of mine, I have zeroed out the MAC address, but you can still see the format.  Your entry would show the PCI device name as 0x168C:0x002A, most likely.

# PCI device 0x8086:0x0083 (iwlagn)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:00", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"

---

### Post by lsutiger on 2012-09-18
Ok, I edited the file and did find the listing for the broadcom, so I commented it out. No go. 
Here is another hint. When I click on the Network Manager, under Wireless Networks, it states wireless is disabled.

---

### Post by lsutiger on 2012-09-18
Also from iwconfig:
wlan0     IEEE 802.11bgn  ESSID: off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=off   
          Retry  long limit:7   RTS thr: off   Fragment thr: off
          Power Management: on

---

### Post by f8l_0e on 2012-09-18
Is there an entry for the current wireless card?

---

### Post by lsutiger on 2012-09-18
Yes:```
# PCI device 0x168c:0x002a (ath9k)
SUBSYSTEM=="net", ACTION=="add", DRIVERS=="?*", ATTR{address}=="00:00:00:00:00:00", ATTR{dev_id}=="0x0", ATTR{type}=="1", KERNEL=="wlan*", NAME="wlan0"
```
(changed mac in post to 0's)

---

### Post by f8l_0e on 2012-09-18
Does the laptop have a physical wifi switch just an Fn key wifi switch? If the mini pci-e card was pulled from the computer after being in radio off mode, it might be stuck in that state.

Check here:

[http://www.linuxquestions.org/questions/linux-wireless-networking-41/wireless-is-disabled-even-with-killswitch-off-834542/]("http://www.linuxquestions.org/questions/linux-wireless-networking-41/wireless-is-disabled-even-with-killswitch-off-834542/")

---

### Post by lsutiger on 2012-09-18
I do have a hardware switch (FN + F3), but it does not work (ie - nothing happens when I push it).
I have tried the following from a post @ askubuntu.com:
Edit /var/lib/NetworkManager/NetworkManager.state
Currently it reads:
NetworkingEnabled=true
WirelessEnabled=false
WWANEnabled=true

I stopped network manager, edited the file to enable wireless and checked it to make sure the changes took. I then restarted network manager. Then the file changed back to wireless not enabled (false)

Also, when I had the broadcom card installed, I did a lot of tutorials on trying to get it working. I may have disabled wireless in some way and did not know exactly what I did, and to boot I did not take notes (I know my fault). I have the wireless card from the old computer which I can install, but want to get this thing working.

---

### Post by lsutiger on 2012-09-18
OK - I took the easy route and swapped wireless cards. On wireless now :)
Thank you for all of your help.

---

### Post by einonm on 2012-09-19
Great stuff. Perhaps you can mark the thread as 'solved' ?

---

