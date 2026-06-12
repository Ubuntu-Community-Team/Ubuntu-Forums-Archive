---
title: "Detects Wireless Driver But No Wireless"
date: 2006-06-18
forum: General Help
---

### Post by blue_thunder on 2006-06-18
I've been trying through the day to set up wireless in Dapper after having no trouble at all in Breezey, but all to no avail. It detecs the "bcmwl5" driver and I enter my ssid and WEP key, but when i try to connect (dhcp) it takes a while and says the connection is active, but when I attempt to start up firefox, no luck.

Any ideas would be greatly appreciated.

Thanks,

Shaun

---

### Post by DarthMandeep on 2006-06-18
What does the iwconfig tool say? Can you ping your router?

---

### Post by blue_thunder on 2006-06-18
iwconfig comes up with: 

```
sthehi07@dhcp81:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11a/b/  ESSID:"belkin54g"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid
          Bit Rate=1 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

```

No luck trying to ping the router.

---

### Post by blue_thunder on 2006-06-18
Any ideas?

---

### Post by shdgrao on 2006-06-18
I have exactly the same problem as you. If you get something please post it.
Thanks.

---

### Post by blue_thunder on 2006-06-18
Still no luck for me. I don't know if it might have something to do with the driver after switching over to dapper...I really don't know.

---

### Post by DarthMandeep on 2006-06-19
Are you using the bcm43xx driver or ndiswrapper? If you are using one, you've got to make sure the other is not loaded. 

What's the output of the lsmod tool?

---

