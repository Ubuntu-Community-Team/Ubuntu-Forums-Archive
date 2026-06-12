---
title: "WEP Key not remembered on boot"
date: 2006-05-13
forum: General Help
---

### Post by gitargr8 on 2006-05-13
Hello, I was able to get pretty far with kubuntu before I had to finally break down and post a question. I was able to get my wifi card working in KDE, but whenever I reboot the settings aren't remembered, specifically the WEP key. 

If I try to run dhclient wlan0 right after boot it hangs on the DHCPREQUEST on wlan0 to 255.255.255.255 port 67 part. This won't work until I do iwconfig wlan0 key restricted <WEPKEY>, after that I can run dhclient and get on the net. 

I've tried editing the /etc/network/interfaces and put the actual wep key in place of the *'s but that doesn't fix it. Thanks for the help.

---

### Post by tsb on 2006-05-14
try here

[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by gitargr8 on 2006-05-14
Well I read through that, but didn't seem to find a solution. I was wondering, is there a way to do a sudo iwconfig wlan0 key restricted XXXX and sudo dhclient wlan0 at boot? I could put it in a script, but I don't know how to autoload it at boot.

---

### Post by acidphex on 2006-05-14
I've got my wlan set up with WEP the way i want it with this wiki:

[https://wiki.ubuntu.com/W:-# iFiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/W:-# iFiHowto?highlight=%28wifi%29)

If you don't wanna' go through the wiki try to look at what i did and see if that works out for you:

**1.** Enter this command in a terminal:> 
```
iwconfig
```

This is what I got:
> $ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b  ESSID:"wireless"
          Mode:Managed  Frequency:2.422 GHz  Access Point: 00:0F:66:21:DD:E1
          Bit Rate=11 Mb/s   Tx-Power=20 dBm
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=84/100  Signal level=-31 dBm  Noise level=-81 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4261   Missed beacon:8

sit0      no wireless extensions.



*This should tell you how your wireless lan card is detected. According to the above mine is **eth1** and connected to a wireless network called *"wireless"* (**ESSID "wireless"** ). Usually the wired lan is detected as **eth0**.

**2.** Then edit the file **/etc/network/interfaces** by doing this:

```
kdesu kate /etc/network/interfaces
```

Then I added this to the end of it (NOTICE: where i used **eth1**):
> auto wlan0
iface eth1 inet dhcp
wireless_essid   homewireless
wireless_key     FEFEFEFEFE
wireless_channel 11
wireless_mode    managed


*Notice next to **wireless_essid** enter your home wirless network name.
*Notice next to **wireless_key** enter your WEP key.

**3.** Save and exit kate.

**4.** Turned off the wire lan:
```
sudo ifdown eth0
```

**5.** Then I used this to turn on the wirless lan(NOTICE: where i used **eth1**):
```
sudo ifup eth1
```

The **ifup** and **ifdown** are used to connect or disconnect to lan interfaces. Now that should do the trick.

---

### Post by CP-Geek on 2006-05-22
This was great, helped me too. I'm moving constantly through 3 different LAN's where one is Wlan. So I made .sh's with profile change, takes about a second, insert connection and click on the shortcut, can't be easier :)

---

