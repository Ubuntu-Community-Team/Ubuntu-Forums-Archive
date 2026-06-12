---
title: "Download speed effectively halved"
date: 2010-02-14
forum: General Help
---

### Post by foens on 2010-02-14
Hello Ubuntu Community.

It is not long since I installed Ubuntu on my desktop, having a dual boot with Windows 7.

I have an internet connection on 12mbit / 1 mbit.

When upgrading with apt-get update or upgrade fetching packages felt very slow, running on only 600kb/s. I thought I was using a slow mirror, but went to a speedtest on my ISP's homepage.

The results was:
Download: 6,33mbit
Upload:  0,73mbit.

Ive tested it multiple times with approximately the same results. So it sounds like my ISP is cheating me, but no!
Results on my Windows 7 is what you would expect:
Download: 12,35mbit
Upload 1,12mbit
which was also tested multiple times.

I have no idea what might be wrong - I have searched Google and found that ipv6 could be a problem, but that only seems to be a problem with DNS resolving, and not with download speeds when DNS has been resolved.

What should I do?

---

### Post by mikewhatever on 2010-02-14
> **foens said:**
> ..........

When upgrading with apt-get update or upgrade fetching packages felt very slow, running on only 600kb/s. I thought I was using a slow mirror, but went to a speedtest on my ISP's homepage.
..........

That was most likely a slow mirror indeed, or a fast one but overloaded. Picking another on should help. As for the rest of your post, offering help would be mere guesswork, without a shred of information on your networking setup.

---

### Post by foens on 2010-02-14
> **mikewhatever said:**
> That was most likely a slow mirror indeed, or a fast one but overloaded. Picking another on should help. As for the rest of your post, offering help would be mere guesswork, without a shred of information on your networking setup.

As I tried to state, it seems that my Ubuntu computer is limited to the 6mbit, which could mean that the mirror was actually fast enough, but something local to Ubuntu limited my bandwidth.

I am unsure what to tell you about my network setup, but here goes a try:
I am running a Desktop computer with a wireless card, which uses closed-source drivers (b43-fwcutter package supplies the drivers if I remember correctly).
With my wireless connection I am connected to a router which is again connected to my ISP through Cable-TV.
I would gladly supply any logs, but I am not aware of which to attend to - I am not an expert in Ubuntu, yet.

PS: Thank you for your reply, I am totally lost in this issue.

---

### Post by OliW on 2010-02-14
Speedtest relies on Flash and given Flash's poor performance everywhere else in Linux, I wouldn't trust its network performance either.

Just download a file. Download this: [http://london1.linode.com/100MB-london.bin](http://london1.linode.com/100MB-london.bin)

It's just a 100meg speedtest file. See what speed you get.

If it's still slow, I'd suggest it might be a limitation of your wireless drivers. I'm not familiar with them so I can't vouch either way.

---

### Post by foens on 2010-02-14
On Windows it started out on 600 but went stable on ~1150 kb/sec
On Ubuntu it went stable on ~750

I then fetched some files from Ubuntu.com, debian.org and others, all hitting a max ~750.

Also, when I saw that my speed on the ubuntu mirrors were slow, I tried changing to others - all with the same results.

What should I do now?

---

### Post by mikewhatever on 2010-02-14
> **foens said:**
> As I tried to state, it seems that my Ubuntu computer is limited to the 6mbit, which could mean that the mirror was actually fast enough, but something local to Ubuntu limited my bandwidth.

That would have been the case if you were downloading with 6,000kbps, but you said it was 600kbps.

> I am unsure what to tell you about my network setup, but here goes a try:
I am running a Desktop computer with a wireless card, which uses closed-source drivers (b43-fwcutter package supplies the drivers if I remember correctly).
With my wireless connection I am connected to a router which is again connected to my ISP through Cable-TV.
I would gladly supply any logs, but I am not aware of which to attend to - I am not an expert in Ubuntu, yet.

PS: Thank you for your reply, I am totally lost in this issue.

Well, it may be useful to know that you use wireless and not wired, and cable and not DSL connections. Do you use the same encryption in Ubuntu as in Windows? Can you post the output of <sudo iwconfig> without brackets. Have you tried testing the speed when connected with an ethernet cable?

---

### Post by foens on 2010-02-14
> **mikewhatever said:**
> That would have been the case if you were downloading with 6,000kbps, but you said it was 600kbps.
Damn. Thought I had the units right. When I mention kbits, it is actually kbytes (so, kb = KB) Sorry!


> **mikewhatever said:**
> Well, it may be useful to know that you use wireless and not wired, and cable and not DSL connections. Do you use the same encryption in Ubuntu as in Windows? Can you post the output of <sudo iwconfig> without brackets. Have you tried testing the speed when connected with an ethernet cable?
I use the exact same wireless access point in both Windows and Ubuntu, but using WPA2-PSK.

I had not thought of testing using only ethernet - it has interesting results:
>1200KB/sec download speed, just as I wanted. It is stable there, both with the file and flash speedtest.


My iwconfig looks as follows:
```
foens@foens-laptop:~$ sudo iwconfig
[sudo] password for foens: 
lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:"WirelessHome"  
          Mode:Managed  Frequency:2.412 GHz  Access Point: 00:17:9A:9B:AB:F0   
          Bit Rate=54 Mb/s   Tx-Power=20 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Encryption key:[SOME KEY HERE] [2]
          Power Management:off
          Link Quality=64/70  Signal level=-46 dBm  Noise level=-65 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

foens@foens-laptop:~$ 

```

But it seems that it is the wireless that is the problem. I have a network capable for the Wireless G standard, could it be that the drivers only connect using the Wireless B standard?
Edit: No, since the iwconfig shows 54Mbit link.

---

### Post by mikewhatever on 2010-02-14
Yes, everything seems to be ok, at least as far as I can tell.

---

### Post by foens on 2010-02-14
> **mikewhatever said:**
> Yes, everything seems to be ok, at least as far as I can tell.

Would that suggest that the drivers are the issue?
Should I report a bug, and where if so?

---

### Post by efflandt on 2010-02-14
Either I missed it or you have not yet mentioned which Ubuntu version you are running and what type of Broadcom wireless device you have (BCM related output of **sudo lspci -v**).  So it may be impossible for anyone else to test (and a waste of time) whether it is a hardware, software, or wireless security issue if they do not have that problem without matching hardware, software version, or type of wireless security (and fast enough internet connection).

By default ipv6 is ignored in Ubuntu 9.10 (or at least that is what Network Connections shows in ipv6 tabs).

The only computer I have using B43 driver in Ubuntu 9.10 for BCM4328 has some other issues (keyboard/mousepad lag), yet its wireless WEP is statistically the same as the 5+ Mbps internet download speed test for anything else on my LAN wired or wireless regardless of OS.  But my DSL connection is not fast enough to tell if I would have an issue like yours at higher speeds.

---

### Post by foens on 2010-02-14
#10
I am using Ubuntu 9.10 64bit desktop.

Here is the relevant information from **sodu lspci -v**:
```

03:00.0 Network controller: Broadcom Corporation BCM4311 802.11b/g WLAN (rev 02)
	Subsystem: Hewlett-Packard Company Device 1375
	Flags: bus master, fast devsel, latency 0, IRQ 16
	Memory at f2000000 (64-bit, non-prefetchable) [size=16K]
	Capabilities: [40] Power Management version 3
	Capabilities: [58] Vendor Specific Information <?>
	Capabilities: [e8] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable-
	Capabilities: [d0] Express Endpoint, MSI 00
	Capabilities: [100] Advanced Error Reporting <?>
	Capabilities: [13c] Virtual Channel <?>
	Capabilities: [160] Device Serial Number 1a-00-e1-ff-ff-73-c1-6a
	Capabilities: [16c] Power Budgeting <?>
	Kernel driver in use: b43-pci-bridge
	Kernel modules: ssb
```

In reply to keyboard/mousepad lag -> This should not be the same I asked about earlier? [http://ubuntuforums.org/showthread.php?p=8819701](http://ubuntuforums.org/showthread.php?p=8819701)

---

### Post by foens on 2010-02-23
bump

I am still having a problem with this, and I have no idea what to do. Is there anyone who knows what the problem might be, or knows someone I can contact?

---

### Post by foens on 2010-02-24
bump

---

