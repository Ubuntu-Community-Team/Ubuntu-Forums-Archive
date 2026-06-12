---
title: "Bad LAN card, a dirver issue or ..."
date: 2012-08-27
forum: General Help
---

### Post by apochry on 2012-08-27
Hello,

yesterday I tried to connect my 6 months old laptop to a LAN network (with a cable) for the first time (since than I've never used the LAN card). What happened was that the laptop  won't auto connect to network on cable plugged in, or even after reboot. Than I thought it's the auto configuring not working, so I tried configuring the card manually - no luck! Than I went to the rooter the card is connected to, to see that the LED indicating connection with a network card is off (I have four LEDs for the four LAN ports at the back, the usual stuff). As far as I know the  LED should light even if the card is not configured right, at least that is what happens when I connect another laptop. So this all makes me think that my LAN card is bad. Or it's maybe a driver issue, which will be kind of odd, will it not...?

The card is detected, thought:[SIZE=2]```
christo@StupiDELL:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 84:8f:69:cd:94:XX  
          inet6 addr: fe80::868f:69ff:fecd:94f7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:173 errors:0 dropped:1939 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:35605 (35.6 KB)
          Interrupt:47 Base address:0x6000 

```[/SIZE]
Moreover:

[LIST]
[*]The cable is OK, I've tried it with another laptop.
[/LIST]

[LIST]
[*]The rooter is also OK, works fine with other laptop connected to the same ports.
[/LIST]

[LIST]
[*] I've tried connecting the "bad" card directly to the modem the rooter is connected to. The LED indicators here stay off too.
[/LIST]

[LIST]
[*]I also booted a live xUbuntu CD to try if things will work on a fresh Linux, but the result was the same.
[/LIST]
 The opinion of someone with better hardware knowledge than me will be much appreciated!


Thank you!

   - Christo

---

### Post by Cheesehead on 2012-08-27
You have done exactly the right things in your troubleshooting so far.
Good job eliminating the cable and router as possibilities!

Next, try the command lspci -v . All of your bus-connected devices will appear. Look for the section that includes your LAN hardware.

For example, 

```
:~$ lspci -v 

05:00.0 Ethernet controller: Atheros Communications Inc. AR8132 Fast Ethernet (rev c0)
	Subsystem: Acer Incorporated [ALI] Device 0213
	Flags: bus master, fast devsel, latency 0, IRQ 42
	Memory at f0200000 (64-bit, non-prefetchable) [size=256K]
	I/O ports at a000 [size=128]
	Capabilities: <access denied>
	Kernel driver in use: atl1c
	Kernel modules: atl1c

```

Look for:
1) Is the LAN card detected at all?
2) On the bottom line is a kernel module assigned? (In this example , atl1c)
3) Is the chipset on the first line supported? (In this example, AR8132)

If the hardware isn't detected at all, then you may have a loose connection or a dead LAN card.

If a kernel module is assigned, then the card is properly detected and configured...but the port may be dead.

If a kernel module is not assigned, it may be as simple as installing the appropriate kernel module for that chipset...once we know the chipset.

---

### Post by Colin R on 2012-08-27
Check the BIOS at power up.  Sounds to me like the wired LAN interface may have been turned off.

---

### Post by apochry on 2012-08-30
> **Colin R said:**
> Check the BIOS at power up.  Sounds to me like the wired LAN interface may have been turned off.
 
Thanks for the suggestion! i don't have an option to disable/enable the card in the BIOS. I have such for camera, mic, fingerprint reader, USBs, eSATA, but not for LAN and WLAN cards.
Nevertheless, reseting the BIOS to its defaults fixed the issue, don't ask me why... :-s

 -Christo

---

### Post by apochry on 2012-08-30
@ [Cheesehead]("http://ubuntuforums.org/member.php?u=425951")

Thanks a lot to you too! "lspci -v" showed the LAN card:
```
04:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 06)
    Subsystem: Dell Device 04c5
    Flags: bus master, fast devsel, latency 0, IRQ 47
    I/O ports at 3000 [size=256]
    Memory at e0404000 (64-bit, prefetchable) [size=4K]
    Memory at e0400000 (64-bit, prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel driver in use: r8168
    Kernel modules: r8168
```... apparently a Realtek RTL8111/8168B one. After some digging on the web I found out, that that some people have similar issues with this particular interface. I than followed the solution suggested by  [praseodym]("http://ubuntuusers.de/user/praseodym/") on a german ubuntu forum, replacing the r8169 kernel driver with the r8168, which should be right for this particular card. This didn't work for me, bun many with similar problems have reported positive result. So here is a [LINK]("http://forum.ubuntuusers.de/topic/lan-karte-funktioniert-nicht/#post-3005217") to to this thread post, unfortunately in German. Google translate could help you there, thought all one needs to do, in order to replace the kernel drivers, is to execute the commands from the first code-box of the post and reboot.

So, at the end of the day, my suggestion to people with problems with this LAN card is to reset BIOS and if it doesn't work to replace the kernel drivers.

- Christo

---

