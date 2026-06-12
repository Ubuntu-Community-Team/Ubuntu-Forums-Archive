---
title: "wireless card help??????????????"
date: 2011-06-02
forum: General Help
---

### Post by miasmablk on 2011-06-02
the wireless in my laptop has stopped working. it's a broadcom BCM-4312 i'm using the same STA driver package that i have been for about 6 months now which was working like a charm, but it has suddenly decided to stop working on me for some reason. The network manager shows that wireless is enabled (for all that matters) but im not getting any signal someone please help. Im kinda a noob at this.

---

### Post by 5149.5 on 2011-06-02
You could run nm-tool. It might give some clues. Paste the result in a new post and enclose it in code tags. (highlight the text and click the # sign at the top of the window.)

---

### Post by miasmablk on 2011-06-02
here is the output for "nm-tool" also I've notice under the network manager tab that "wireless disabled by hardware switch" is grayed out yet when I toggle the switch on my keyboard responsible for enabling/ disabling wireless it has no effect..  P.S i've edited some of the info...ya know :P




- Device: eth1 -----------------------------------------------------------------
  Type:              802.11 WiFi
  Driver:            wl
  State:             unavailable
  Default:           no
  HW Address: 00:00:00:00:00:00

  Capabilities:

  Wireless Properties
    WEP Encryption:  yes
    WPA Encryption:  yes
    WPA2 Encryption: yes

  Wireless Access Points 


- Device: eth0  [Auto eth0] ----------------------------------------------------
  Type:              Wired
  Driver:            sky2
  State:             connected
  Default:           yes
  HW Address:        00:00:00:00:00:00

  Capabilities:
    Carrier Detect:  yes
    Speed:           100 Mb/s

  Wired Properties
    Carrier:         on

  IPv4 Settings:
    Address:         192.000.0.000
    Prefix:          24 (255.255.255.0)
    Gateway:         192.168.1.254

    DNS:             192.168.1.254

---

### Post by 5149.5 on 2011-06-02
Your driver is: wl  That doesn't look right. The state shows: unavailable  Is it possible your wireless is disabled in BIOS? Check that driver.

---

### Post by miasmablk on 2011-06-02
i Think I've fixed it i went into startup applications and edited the network manager command line from **nm-applet --sm-disable** to **nm-applet --sm-enable** and now my wireless works again... 

this fix worked for ubuntu 11.04 x86_64 on a dell 1545 for a Broadcom BCM4312- wireless card

---

### Post by 5149.5 on 2011-06-02
Good job.

---

