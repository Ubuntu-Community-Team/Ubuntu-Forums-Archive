---
title: "wireless networks greyed out"
date: 2012-05-13
forum: General Help
---

### Post by Pacopag on 2012-05-13
Hi. I just did a fresh install of Lubuntu 12.04 on a Dell Inspiron 1720 laptop.  Install went fine (what a great installer!).

Now I'm all logged in, but when I click the network manager icon at the bottom right, "Wireless Networks" is greyed out.  I've installed *buntu on dozens of computers and never had a problem with hardware detection, so I'm not sure where to begin.  Here's the output of iwconfig
```

lo        no wireless extensions.

eth2      no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on

```
Any help would be great.  Thanks.

Edit:  I just remembered that upon first startup I go a pop-up message saying "Restricted drivers are available..." but I didn't have time to read the whole message.  What is this message all about?  Could it have something to do with my problem?

Edit:  I found the driver on the dell website.  I extracted the .exe and located the .inf file, so I'm pretty sure I can figure out how to use ndiswrapper to install the driver from dell.  But the documentation says
"Before you install any wireless driver with ndiswrapper or ndisgtk, make sure there are no other drivers trying to use your wireless card. If there are, your ubuntu may freeze."
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

lshw
```

 *-network DISABLED
       description: Wireless interface
       physical id: 2
       logical name: wlan0
       serial: 00:1e:4c:08:3b:5a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes driver=b43 driverversion=3.2.0-24-generic firmware=N/A link=no multicast=yes wireless=IEEE 802.11bg

```
This looks to me like a drive IS installed, but DISABLED.  Where to go from here?

---

### Post by sammiev on 2012-05-13
Have you went to System Settings and selected Additional Drivers yet?

---

### Post by Pacopag on 2012-05-13
Not sure where to find that in Lubuntu.  A quick look through all the menus turns up nothing.

lshw shows that b43 driver is being used, but that the card is disabled.

I notice a physical switch on the side of the laptop for turning on/off the wireless.  The switch is in the "on" position, but the little light is not lit up.  I tried switching it off and on, but that didn't work.

---

### Post by Pacopag on 2012-05-13
ok.  I've determined that the problem is missing firmware.  Now, what would be easier or better: 1) blacklist the b43 driver (how do I do that?) and install the proprietary driver via ndiswrapper, or 2) install the proper linux-native firmware
?

---

### Post by Pacopag on 2012-05-14
I tried ndisgtk first.  It didn't work because it "Failed to load the ndiswrapper module", which seemed to be installed.

So then I just installed the package "firmware-b43-installer" and everything works now.

Cheers.

---

