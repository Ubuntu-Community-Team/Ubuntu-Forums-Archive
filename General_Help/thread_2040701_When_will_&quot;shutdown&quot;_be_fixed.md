---
title: "When will &quot;shutdown&quot; be fixed?"
date: 2012-08-11
forum: General Help
---

### Post by Mr. Beekeeper on 2012-08-11
Is there a way to tell when the "shutdown" command Ubuntu and Xubuntu be fixed?  I'm going to have to switch to another distro, because this bug has completely disabled my Wake on  Lan (WOL).  I've tried every permutation of "halt", "poweroff" and "shutdown" from the command line, and the system either hangs or turns off, but not properly (WOL no longer works).  This used to work with previous versions:

```
sudo halt now
```

Thanks.

---

### Post by CharlesA on 2012-08-11
halt only halts now.

You need to use this:

```
sudo poweroff now
```

See here: [https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240](https://bugs.launchpad.net/ubuntu/+source/upstart/+bug/880240)

Particularly comment 47, 48 and 49.

In any case, I haven't tried WoL on my Ubuntu box, but it should be handled by the BIOS if the machine is in a "soft off" state.

EDIT: I just tested it on both Windows and Fedora and WoL works fine from either poweroff or suspend.

I would suspect your PC hardware doesn't support WoL, if it isn't working.

---

### Post by Mr. Beekeeper on 2012-08-11
After entering :

```
sudo poweroff now
```

The system will not wake from lan, indicating an improper shutdown.  

I now see that the problem will never be fixed.  

Any good recommends on a non-ubuntu distro?  This problem has broken my setup.  Thanks for the reply.

---

### Post by Mr. Beekeeper on 2012-08-11
I have been using WOL for about 8-9 months now, so I know my hardware supports it.  I have verified via WireShark that the packets were being sent.  I tried to wake from my phone and from my netbook, both of which worked before, to no avail.


:(

---

### Post by CharlesA on 2012-08-11
What version are you using? I just booted a 12.04 livecd, suspended it and then powered if off and WoL worked for both.

I do not believe it is a problem with the OS.

If you are looking for an alternative to Ubuntu, you could look at either Debian or Fedora. I prefer Fedora, but that is just me.

Make sure you are using the proper MAC/IP/hostname for the magic packet. I just found out I had my dhcp leases configured incorrectly when I went to test this, so make sure that is correct. ;)

---

### Post by lisati on 2012-08-11
Just a random thought, possibly irrelevant: has the relevant setting in BIOS been messed up somehow?

---

### Post by CharlesA on 2012-08-11
I just tested it from my other Ubuntu 12.04 box and ran this command:

```
sudo etherwake -b 12:34:56:78:90:ab
```

Where 12:34:56:78:90:ab is the target machine's MAC address.

Worked fine for me.

---

### Post by Mr. Beekeeper on 2012-08-11
Thanks for the replies!  I sextuple confirmed that the proper BIOS settings were enabled.  I don't remember changing any router settings, since I'm waking over the local network.  I have my server locked to 192.168.1.3 (I'm trying to wake it up.)

Thanks again!

---

### Post by CharlesA on 2012-08-11
Are you using the IP address or MAC when trying to wake it up?

---

### Post by asmoore82 on 2012-08-11
I thought this was by design.

Computers I've seen definitely turn off their NIC after being interactively shutdown.

In other words, this is the normal pattern of behaviour I've seen:

1. Start with PC with LAN connection and now power cord.
2. Plug in power cord, PC remains off, NIC lights up.
3. Power on PC, use normally.
4. Shutdown PC normally, NIC no longer lights.

I've seen this in a lab full of XP machines as well, not just Ubuntu. The reason I have specifically tracked this behaviour is that powered off PC's with active NIC's interfere with high speed broadcast/multicast traffic. I assume it affects WOL as well; the NIC can't receive WOL if it's off.

In my case, NIC off is the desired behaviour, so that it doesn't pull the multicast down. In your case, NIC on is what you want for WOL. So the workaround might be to flip your power strip off and back on again right after shutting down your PC.

---

### Post by Mr. Beekeeper on 2012-08-11
> **CharlesA said:**
> Are you using the IP address or MAC when trying to wake it up?


MAC address, with an -i wlan0, since my netbook (the waker) is wireless where my server (the wakee?) is on the wired LAN.

```
sudo etherwake -i wlan0 00:50:8d:e9:45:98
```

---

### Post by Mr. Beekeeper on 2012-08-11
> **asmoore82 said:**
>  So the workaround might be to flip your power strip off and back on again right after shutting down your PC.

I tried this, but it didn't work either.  Thanks everyone for all the help.

---

### Post by CharlesA on 2012-08-11
> **asmoore82 said:**
> I thought this was by design.

Computers I've seen definitely turn off their NIC after being interactively shutdown.

The PC I was testing with has no lights on the NIC even tho it has power. The port it is plugged into on the switch shows a light tho.

> **Mr. Beekeeper said:**
> MAC address, with an -i wlan0, since my netbook (the waker) is wireless where my server (the wakee?) is on the wired LAN.

```
sudo etherwake -i wlan0 00:50:8d:e9:45:98
```

Hrm, I didn't try it with the interface switch. Maybe try it without?

---

### Post by Mr. Beekeeper on 2012-08-11
Wireshark is showing the packets sent to 192.168.1.255 even though the DHCP range on the router only goes to 192.168.1.254 and can't be changed to 192.168.1.255.

Thanks!

---

### Post by CharlesA on 2012-08-11
> **Mr. Beekeeper said:**
> Wireshark is showing the packets sent to 192.168.1.255 even though the DHCP range on the router only goes to 192.168.1.254 and can't be changed to 192.168.1.255.

Thanks!
That is how it is supposed to work. 192.168.1.255 is the broadcast address, it sends the packet to all machines on the network, but only the one with the referenced MAC will wake up.

---

### Post by Mr. Beekeeper on 2012-08-11
> **CharlesA said:**
> That is how it is supposed to work. 192.168.1.255 is the broadcast address, it sends the packet to all machines on the network, but only the one with the referenced MAC will wake up.


Thanks.  The phone and my netbook show slightly different packets, but neither one works.  Maybe my motherboard is shot.

---

### Post by CharlesA on 2012-08-11
> **Mr. Beekeeper said:**
> Thanks.  The phone and my netbook show slightly different packets, but neither one works.  Maybe my motherboard is shot.
Maybe. Have you tried a livecd from a different Distro just to be sure?

I tested WoL from my laptop with 12.04 using wakeonlan which is in the main repos and etherwake in the universe repos:

```
sudo wakeonlan 12:34:56:78:90:ab
```

```
sudo etherwake -b -i wlan0 12:34:56:78:90:ab
```

Maybe try wakeonlan and see what happens? It looks like I had to specify which interface to use on my laptop cuz it has both ethernet and wifi.

---

### Post by Mr. Beekeeper on 2012-08-11
I FIXED IT!!!!!!!!!!!!!  WOOHOO!!!!!!!!!

I had to run this:

```
sudo ethtool -s eth2 wol g
```


I ran ifconfig to determine the interface (eth2 is odd, but whatever...)

shutdown using:

```
sudo poweroff now 
```

and it works again!!!

so, as a list, to get WOL working in 12.04, you have to:

1) Set up the settings in your Bios Correctly
2) Run the "ethtool" command above, using the correct interface (eth0, eth1, etc)
3) Power the computer down using the command above

*When in doubt, RTFM!*

[https://help.ubuntu.com/community/WakeOnLan](https://help.ubuntu.com/community/WakeOnLan)

---

### Post by CharlesA on 2012-08-11
I didn't have to manually enable WoL, but it is good you got it working. :)

---

### Post by Mr. Beekeeper on 2012-08-11
> **CharlesA said:**
> I didn't have to manually enable WoL, but it is good you got it working. :)

I hope it helps someone in the future. Thanks so much for your help!  Ubuntu community is awesome!

---

### Post by CharlesA on 2012-08-11
> **Mr. Beekeeper said:**
> I hope it helps someone in the future. Thanks so much for your help!  Ubuntu community is awesome!
You are very welcome. :)

---

