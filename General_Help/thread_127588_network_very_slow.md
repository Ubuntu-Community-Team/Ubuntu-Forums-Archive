---
title: "network very slow"
date: 2006-02-09
forum: General Help
---

### Post by ashrack on 2006-02-09
I am using the onboard NIC on ASUS A7N8X-X which has NFORCE2 chipset.
But when I transfer data thru LAN from another computer the speed is only 3MB/s but from WinXP I get 8MB/s throughput. 
DMA is enabled on the HDD and also buffered read test from HDPARM shows arround 40MB/s. So the HDD is definetly not the problem. And am using the NATIVE NFORCE2 drivers

---

### Post by ashrack on 2006-02-11
what, no sollution? SHould I install NFORCE2 drivers from NVIDIA?

---

### Post by SWAT on 2006-02-11
[QUOTE=ashrack]what, no sollution?...[/QUOTE]Please don't be so illogical, we do this in our FREE time. The question is, HOW did you test the throughput? I've got a NForce3 chipset here, still no problems and perfect throughput (without Nvidia drivers)

---

### Post by handy on 2006-02-11
[QUOTE=SWAT]Please don't be so illogical, we do this in our FREE time. The question is, HOW did you test the throughput? I've got a NForce3 chipset here, still no problems and perfect throughput (without Nvidia drivers)[/QUOTE]

Ditto...

---

### Post by ashrack on 2006-02-11
[QUOTE=SWAT]Please don't be so illogical, we do this in our FREE time. The question is, HOW did you test the throughput? I've got a NForce3 chipset here, still no problems and perfect throughput (without Nvidia drivers)[/QUOTE]
In NAUTILUS and also in KONQUERER they measured throughput of around 2-3MB/s at max with a 700MB file.

---

### Post by ashrack on 2006-02-12
as I checked other forums I see lots of ppl have similar problems. 
I quote one of them
> just copying over samba off my windows pc the gigabit lan we have here and linux always copys very slowly from and to it, is this a bug or something? is there someway i can speed it up, currently copying at about 1.5mb/s instead of the usuall 10-20mb/s.


HAve their been any known sollutoin to this problem?

---

### Post by pt78 on 2006-02-12
And what about duplex setting? Did you check/play with that?

---

### Post by ashrack on 2006-02-12
[QUOTE=pt78]And what about duplex setting? Did you check/play with that?[/QUOTE]
The only thing I did was set the IP to STATIC.

```
tom@pegasus:~$ sudo ethtool eth0
Settings for eth0:
        Supported ports: [ MII ]
        Supported link modes:   10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full
                                100baseT/Half 100baseT/Full
        Advertised auto-negotiation: Yes
        Speed: 100Mb/s
        Duplex: Full
        Port: MII
        PHYAD: 1
        Transceiver: externel
        Auto-negotiation: on
        Supports Wake-on: g
        Wake-on: d
        Link detected: yes

```
IS this correct?

---

### Post by pt78 on 2006-02-12
It is command line tool, you can run it as follows:
sudo mii-tool

---

### Post by ashrack on 2006-02-12
```
tom@pegasus:~$ sudo mii-tool
SIOCGMIIPHY on 'eth0' failed: Operation not supported
no MII interfaces found

```
this is what I get

---

### Post by ashrack on 2006-02-12
apperantly I found my own sollution.
I switched from SMBFS to CIFS
Still testing it, bo so far so good

---

