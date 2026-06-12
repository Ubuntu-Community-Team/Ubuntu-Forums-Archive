---
title: "Wireless Network Help Needed"
date: 2010-03-14
forum: General Help
---

### Post by puddlejumper on 2010-03-14
I have just returned from a trip on which I took my laptop.  The hotel I stayed at had wired network access only.  I used this network with a cat-5 cable connection.

When I returned home, my wireless network connection was not working.  I get the message "Firefox cannot find the server at www.google.com" when I bring up Firefox.  I get the message "error while fetching mail" when I bring up Evolution.

I have desktop Ubuntu based systems which are working correctly.

Everything was working perfectly on the laptop before I left.

Any help would be appreciated.

Thanks.

My laptop is a System 76 Bonobo system.
Bon-P3
Bluetooth
ATI Mobility Radeon HD 4570 Graphics with 513 MB GDDR2 Memory
250 GB Hard Drive 7200 RPM SATA II
2GB DDR3 1066 MHZ (1 DIMM)
9.10 Karmic Koala 64 bit Linux
i5-520M Processor
Wireless Intel wi-fi 5100 80211-a/g/n

linksys simultaneous dual-band wireless router

---

### Post by mikewhatever on 2010-03-14
Are you connected to the router? Can you post the output of **nm-tool** command from a Terminal.

---

### Post by puddlejumper on 2010-03-14
I just connected the laptop directly to the router via a cat-5 cable and enabled the wired network.  All works as it should.  When I enable wireless networks, the system says that the linksys wireless network is available.  When I bring it up and attempt to use it, I get the same problems that I originally reported.

I assume that I am doing something really stupid.  However, I don't know what that might be and am getting more and more frustrated.

---

### Post by mikewhatever on 2010-03-14
Try connecting wirelessly  again, then run the following in a Teminal:

**nm-tool > ~/Desktop/wireless.txt**

The command will generate a text file on your desktop, please attach it to the next post.

While at it, you might want to try and ping google.com:

**ping -c4 74.125.43.147**

If you get a response, it's a DNS problem.

---

### Post by puddlejumper on 2010-03-14
ping -c4 74.125.43.147 resulted in the following
Ping 74.125.43.147 (74.125.43.147) 56(84)Bytes of data

74.125.43  .147 Ping statistics
4 Packets of data transmitted, 0 received, 100% packet loss, time 3007ms


NetworkManager Tool

State: connected

- Device: wlan0  [Auto linksys] ------------------------------------------------
  Type:              802.11 WiFi
  Driver:            iwlagn
  State:             connected
  Default:           yes
  HW Address:        00:24:D6:59:6B:C2

  Capabilities:
    Speed:           54 Mb/s

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points (* = current AP)
    *linksys:        Infra, 00:23:69:D9:65:BA, Freq 2462 MHz, Rate 54 Mb/s, Strength 100 WPA

  IPv4 Settings:
    Address:         192.168.1.102
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.1

    DNS:             192.168.1.1


- Device: eth0 -----------------------------------------------------------------
  Type:              Wired
  Driver:            jme
  State:             unavailable
  Default:           no
  HW Address:        00:90:F5:9A:CA:19

  Capabilities:
    Carrier Detect:  yes
    Speed:           10 Mb/s

  Wired Properties
    Carrier:         off

---

### Post by mikewhatever on 2010-03-16
The problem got solved in another thread, apparently, something router related.
[http://ubuntuforums.org/showthread.php?t=1430370](http://ubuntuforums.org/showthread.php?t=1430370)

---

