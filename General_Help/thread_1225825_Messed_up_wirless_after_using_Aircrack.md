---
title: "Messed up wirless after using Aircrack"
date: 2009-07-29
forum: General Help
---

### Post by BeastMode on 2009-07-29
OK, so I was messing around with Aircrack and all typically related programs.  (airodump, aireplay, etc...)

I actually got it all to work, which was pretty cool!

But now that I have done all that, I can't connect to any of my wireless networks anymore.  They don't even show up when I click on the network icon up top.

I use Ubuntu 9.04 UNR.  Acer Aspire One with an Atheros card.

Any chance I can get some help without having to re-install Ubuntu?

---

### Post by rudi009 on 2009-07-29
post the output of iwconfig

---

### Post by BeastMode on 2009-07-29
> **rudi009 said:**
> post the output of iwconfig

Yes, Sir.

Since I obviously can't be on the 'net on the computer in question, I'll just paraphrase.

lo           no wireless extensions.

eth0         no wireless extensions.

wmaster0     no wireless extensions.

wlan0        IEEE 802.11bg ESSID.""
             Mode:managed Frequency:2.412 GHz Access Point:     Not associated.
              Power management off...bunch of other stuff.  Let me know if you need it.


pan0          No wireless extensions

---

### Post by rudi009 on 2009-07-29
couldn't see the problem..is wireless enabled?? right click on the network icon.

---

### Post by BeastMode on 2009-07-29
Yes, Sir.

It's enabled.

---

### Post by t4thfavor on 2009-07-29
If you posted the entire output of iwconfig, the error is probably in there.
Youll be looking for txpower = off. I remember with atheros that they create another "wlanX" device for the monitor mode device so as long as its not showing you have another issue.

It should also be noted that the ath5k drivers kinda suck at the moment, and this would never have happened with an older Madwifi driven card.

Your card is probably just "stuck" you may be able to unstuck it by running /etc/init.d/networking restart (or whatever the network script is), or removing, and reinserting the driver module..

Have you rebooted the PC, that should probably fix it as well.

---

### Post by BeastMode on 2009-07-29
If all else fails, is there a way to just reset everything wireless back to "OEM" settings so that it can become usable again?

It worked "out of the box" after install...just not since I got to playing around with WEP decryption.

---

### Post by BeastMode on 2009-07-29
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.




Flash cards are wonderful things.  And I have no idea how the little smiley faces got into this post!

---

### Post by t4thfavor on 2009-07-29
Its called backup your home dir, and reinstall.

That shouldn't be nessecary though. You should be able to figure this out.

---

### Post by BeastMode on 2009-07-29
> **t4thfavor said:**
> If you posted the entire output of iwconfig, the error is probably in there.
Youll be looking for txpower = off. I remember with atheros that they create another "wlanX" device for the monitor mode device so as long as its not showing you have another issue.

It should also be noted that the ath5k drivers kinda suck at the moment, and this would never have happened with an older Madwifi driven card.

Your card is probably just "stuck" you may be able to unstuck it by running /etc/init.d/networking restart (or whatever the network script is), or removing, and reinserting the driver module..

Have you rebooted the PC, that should probably fix it as well.


Rebooting didn't work.  Anything more on that network script?

---

### Post by t4thfavor on 2009-07-29
> **BeastMode said:**
> lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=0 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.




Flash cards are wonderful things.


run 

```

sudo iwconfig wlan0 txpower 100mw

```

it will set the transmit to something other than 0, which should help you connect.

---

### Post by BeastMode on 2009-07-29
> **t4thfavor said:**
> run 

```

sudo iwconfig wlan0 txpower 100mw

```

it will set the transmit to something other than 0, which should help you connect.

Need I reboot after this?  Initially nothing is happening.  Will reboot now.

Upon reboot, still nothing.

---

### Post by t4thfavor on 2009-07-29
Check the txpower after the reboot, it should say something like. It actually should say something like that after executing the command I gave you, but if not, a reboot is always good :) 

```

wlan0     IEEE 802.11bg  ESSID:"NBIDavison"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:8C:90:B6   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=39/100  Signal level:-67 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

---

### Post by BeastMode on 2009-07-29
> **t4thfavor said:**
> Check the txpower after the reboot, it should say something like. It actually should say something like that after executing the command I gave you, but if not, a reboot is always good :) 

```

wlan0     IEEE 802.11bg  ESSID:"NBIDavison"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:22:6B:8C:90:B6   
          Bit Rate=9 Mb/s   Tx-Power=20 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality=39/100  Signal level:-67 dBm  Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```



After the reboot, it said 0.  Now that I have run the command again (and haven't rebooted, yet) it does say the 20dbm.

---

### Post by BeastMode on 2009-07-29
I don't know if this helps, but before I started screwing with this thing, my wireless card was actually named ath0.

I see no reference to that here now.

---

### Post by BeastMode on 2009-07-29
Huh.

After the reboot, the txpower went back down to 0 again.

Why would that be?

---

### Post by t4thfavor on 2009-07-29
The driver changed. Madwifi uses athX ath5/9k uses wlanX.

we need to find out what card you have.

```

sudo lshw

```

youll see something like this.

```

-network:1
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: wmaster0
                version: 01
                serial: 00:19:7d:66:8d:80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless

```

---

### Post by BeastMode on 2009-07-29
> **t4thfavor said:**
> The driver changed. Madwifi uses athX ath5/9k uses wlanX.

we need to find out what card you have.

```

sudo lshw

```

youll see something like this.

```

-network:1
                description: Wireless interface
                product: AR2413 802.11bg NIC
                vendor: Atheros Communications Inc.
                physical id: 2
                bus info: pci@0000:06:02.0
                logical name: wmaster0
                version: 01
                serial: 00:19:7d:66:8d:80
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list logical ethernet physical wireless

```

 *-network DISABLED 
                description: Wireless interface 
                product: AR242x 802.11abg Wireless PCI Express Adapter 
                vendor: Atheros Communications Inc. 
                physical id: 0 
                bus info: pci@0000:03:00.0 
                logical name: wmaster0 
                version: 01 
                serial: 00:24:2c:0c:52:70 
                width: 64 bits 
                clock: 33MHz 
                capabilities: pm msi pciexpress msix bus_master cap_list logical ethernet physical wireless 
                configuration: broadcast=yes driver=ath5k_pci latency=0 module=ath5k multicast=yes wireless=IEEE 802.11bg 



Me thinks that whole "disabled" thingy is some sort of a problem.

---

### Post by t4thfavor on 2009-07-29
More than likely, I found a thread here

[http://ubuntuforums.org/showthread.php?p=7695005](http://ubuntuforums.org/showthread.php?p=7695005)

Did you perhaps install any updates when aircracking? It appears a newer kernel broke some wireless chipsets recently. It appears yours is included.

You can check your kernel version by typing uname -a into a console.


Try to rmmod the ath5k driver, and then modprobe ath_pci

Were going to unload the ath5k driver, and load the older one that makes ath0.
```

sudo rmmod ath5k
sudo modprobe ath_pci

```
Check if it works then, and if not folow the instuctibles on the link I sent.


Its after 2AM here, Im going to bed, I will check back in the morning.

---

### Post by BeastMode on 2009-07-29
> **t4thfavor said:**
> More than likely, I found a thread here

[http://ubuntuforums.org/showthread.php?p=7695005](http://ubuntuforums.org/showthread.php?p=7695005)

Did you perhaps install any updates when aircracking? It appears a newer kernel broke some wireless chipsets recently. It appears yours is included.

You can check your kernel version by typing uname -a into a console.


Try to rmmod the ath5k driver, and then modprobe ath_pci

Were going to unload the ath5k driver, and load the older one that makes ath0.
```

sudo rmmod ath5k
sudo modprobe ath_pci

```
Check if it works then, and if not folow the instuctibles on the link I sent.


Its after 2AM here, Im going to bed, I will check back in the morning.

I have to get near an actual ethernet port to try the fix in the link you provided, but the above code didn't work for me.

I don't think this has anything to do with a kernel update.  What I think has happened is that while I was messing around with WEP stuff, I disabled the Wireless device to enable monitoring...and now I don't know how to get it back...possibly.

This post is more of a bump than anything else, however.

---

### Post by t4thfavor on 2009-07-29
try 
```


sudo modprobe -r ath5k
sudo modprobe ath_pci

```

The site link I provided seems to show your exact problem, perhaps ir just appears that the problem occurred after the aircrack events.


It's pretty convincing that alot of people with your same card, and an up-to-date kernel have the same issue.

---

### Post by BeastMode on 2009-07-29
Well..OK.

I turned my computer on just now, and it works.

Wish I could remember the last thing I did last night, as it was late, but whatever it was worked, apparently.

As soon as someone now tells me how to mark a thread as solved, I will do that here.  Thanks for the help!

---

### Post by BeastMode on 2009-07-29
> **t4thfavor said:**
> try 
```


sudo modprobe -r ath5k
sudo modprobe ath_pci

```

The site link I provided seems to show your exact problem, perhaps ir just appears that the problem occurred after the aircrack events.


It's pretty convincing that alot of people with your same card, and an up-to-date kernel have the same issue.

I think the last thing I did was the previous code that you copied into the forum last night.  It didn't immediately work, and I can't remember if I rebooted the computer and tried it again...but this time I booted it with the ethernet jack plugged in (not sure if that means anything) but now the wireless works.  So, I think you solved my problem.

---

### Post by t4thfavor on 2009-07-29
Shouldnt't matter about the ethernet jack, but I'm glad it working. Out of curiosity, do you have a wlan0, or an ath0 now?

---

