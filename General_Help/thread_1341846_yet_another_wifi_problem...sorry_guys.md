---
title: "yet another wifi problem...sorry guys"
date: 2009-11-30
forum: General Help
---

### Post by maximilianyuen on 2009-11-30
I know there are bunch of wifi connection rpboelm for notebook running ubuntu...but still I wanna seek your help
 
My problem:
my notebook is Asus Pro8B, and I installed ubuntu 9.10 64bit (I tried 32bit version, same problem)

my home wifi works fine wit my macbook, imac, and this same asus notebook under windows 7
 
first with Network-Manager, i got the classic wifi disconnect-reconnect-password issues
I read that the built-in Network-manager may not work well and some said using wicd works better

and so I did
 
the first day I switch to wicd, the same problem occur. once in a while the signal drop to red and disconnect, and it reconnect again...

still which makes internet browsing impossible
 
and two days later, without changing anything, it can't even detect my home wifi network just a meter away (in a meter range it can detect in a red bar, which still cant establish connection)
 
just wanna know what other things can I try to resolve this problem...
 
Please help :(

---

### Post by mikewhatever on 2009-11-30
There might be several things to try, but you should start with telling something about your wireless hardware. If that baffles you, open Applications->Accessories->Terminal and post the output of the following command:
```
sudo lshw -C network
```

---

### Post by maximilianyuen on 2009-11-30
> **mikewhatever said:**
> There might be several things to try, but you should start with telling something about your wireless hardware. If that baffles you, open Applications->Accessories->Terminal and post the output of the following command:
```
sudo lshw -C network
```

sorry your code seems not working....

so I took the liberty to just use sudo lshw and choose the network part if thats what you need...

thanks

           *-network
                description: Wireless interface
                product: AR9285 Wireless Network Adapter (PCI-Express)
                vendor: Atheros Communications Inc.
                physical id: 0
                bus info: pci@0000:02:00.0
                logical name: wmaster0
                version: 01
                serial: 00:25:d3:bf:78:f4
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list logical ethernet physical wireless
                configuration: broadcast=yes driver=ath9k latency=0 multicast=yes wireless=IEEE 802.11bgn
                resources: irq:17 memory:feaf0000-feafffff

---

### Post by mikewhatever on 2009-11-30
Having looked around, it seems like one suggested solution is to install linux-backports-modules-karmic. Hope that works. Generally speaking, Broadcom and Atheros cards still don't play nicely with Linux.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA)

---

### Post by Bucky Ball on 2009-11-30
> **mikewhatever said:**
> Generally speaking, Broadcom and Atheros cards still don't play nicely with Linux.


I have Broadcom in my laptop and have installed several Atheros cards and they have all worked 'out of the box' since 8.04. I could NEVER get the Broadcom working in 7.04. Installed 8.04 and the card was picked up, I was asked the appropriate questions, followed my nose and had wireless in about 5 minutes. Same with the Atheros. 

You have probably plugged an ethernet cable in. Does that work? Have you gotten ALL updates while online? If not, System->Administration->Update Manager. 

Try System->Administration->Hardware Drivers. Is there anything disabled in there for wireless?

System->Admin->Network. Are all the details in there a match for your router? Uncheck disable roaming. Is your router serving you an IP (DHCP server)? 

Config: Auto Config (DHCP)

... and from a terminal, the result of:
```

iwconfig
```

---

### Post by maximilianyuen on 2009-12-01
> **mikewhatever said:**
> Having looked around, it seems like one suggested solution is to install linux-backports-modules-karmic. Hope that works. Generally speaking, Broadcom and Atheros cards still don't play nicely with Linux.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA)

thanks, will do :p

---

### Post by maximilianyuen on 2009-12-01
> **Bucky Ball said:**
> I have Broadcom in my laptop and have installed several Atheros cards and they have all worked 'out of the box' since 8.04. I could NEVER get the Broadcom working in 7.04. Installed 8.04 and the card was picked up, I was asked the appropriate questions, followed my nose and had wireless in about 5 minutes. Same with the Atheros. 

You have probably plugged an ethernet cable in. Does that work? Have you gotten ALL updates while online? If not, System->Administration->Update Manager. 

Try System->Administration->Hardware Drivers. Is there anything disabled in there for wireless?

System->Admin->Network. Are all the details in there a match for your router? Uncheck disable roaming. Is your router serving you an IP (DHCP server)? 

Config: Auto Config (DHCP)

... and from a terminal, the result of:
```

iwconfig
```


yes i have done all update via cable before switching to wicd

but today i check it said there is error durring signature verification...is that becoz i am not using network manager/ otherwise everything else should be the same

message----------------------------------------------------------
W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://hk.archive.ubuntu.com](http://hk.archive.ubuntu.com) karmic-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: Failed to fetch [http://hk.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release](http://hk.archive.ubuntu.com/ubuntu/dists/karmic-updates/Release)  

W: Some index files failed to download, they have been ignored, or old ones used instead.

--------------------------------------------------------------------------------

and hardware update didn't show any possible update at the beginning

i don't know what should i look up in the network tool....

the result of the iwconfig:

wlan0     IEEE 802.11bgn  ESSID:"Airport"  
          Mode:Managed  Frequency:2.462 GHz  Access Point: Not-Associated   
          Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by maximilianyuen on 2009-12-01
> **mikewhatever said:**
> Having looked around, it seems like one suggested solution is to install linux-backports-modules-karmic. Hope that works. Generally speaking, Broadcom and Atheros cards still don't play nicely with Linux.

[https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA](https://wiki.ubuntu.com/HardwareSupport/Machines/Netbooks#Asus%20Eee%20PC%201005HA)

well it cant detect my network first, but after i reinstall wicd it seems working fine

at least no disconnect at the past 5 min:p

---

### Post by mikewhatever on 2009-12-01
maximilianyuen, hope your wireless keeps working. The errors you've posted are repository related, and not wicd related. You might want to try another server from System->Admin->Software Sources.

> **Bucky Ball said:**
> I have Broadcom in my laptop and have installed several Atheros cards and they have all worked 'out of the box' since 8.04. I could NEVER get the Broadcom working in 7.04. Installed 8.04 and the card was picked up, I was asked the appropriate questions, followed my nose and had wireless in about 5 minutes. Same with the Atheros. server)? 

You must have been lucky, cause a quick look through the network&wireless subsection reveals that Broadcom and Atheros products are uncontested champions in support requests. That said, I also have a dell mini 10 with BMC4312, which worked out of the box.

---

### Post by maximilianyuen on 2009-12-01
> **mikewhatever said:**
> maximilianyuen, hope your wireless keeps working. The errors you've posted are repository related, and not wicd related. You might want to try another server from System->Admin->Software Sources.


You must have been lucky, cause a quick look through the network&wireless subsection reveals that Broadcom and Atheros products are uncontested champions in support requests. That said, I also have a dell mini 10 with BMC4312, which worked out of the box.

the wifi is working 
thanks both of you:D

and about the update, it only have two choices, Hong Kong and Main Server

both giving me error message :(

and all the Package that fail to download are all "Translation-en_HK "....

---

