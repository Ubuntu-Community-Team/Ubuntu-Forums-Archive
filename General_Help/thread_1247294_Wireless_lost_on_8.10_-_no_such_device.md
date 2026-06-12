---
title: "Wireless lost on 8.10 - no such device"
date: 2009-08-22
forum: General Help
---

### Post by SuaSwe on 2009-08-22
OK, a bit of a story here...

I've been trying to sort out a GRUB menu issue on my neighbour's computer (dual-boot with two hard drives, one with XP and another with Ubuntu) all day. As all Super Grub ISO's I tried turned out to be unbootable I was in the end not able to use it to restore the problem, so after much head-scratching I finally gave up and reinstalled Ubuntu with a 8.10 LiveCD (Jaunty was installed prior to this) without formatting the drives. The partitions (root, swap and home) have been restored with the data on /home/ still present, however some notable issues have occurred:

- The wireless does not work (it works in Windows and worked in Ubuntu until this problem started occurring)
- The sound does not work (ditto)
- There are two kernels listed in GRUB (ending .7 and .14 respectively) and the PS/2 mouse will not work when using .14; a USB mouse was tried on that kernel and worked fine

Now, I have a feeling that if I can get the internet to work, everything else can be sorted out by letting Ubuntu upgrade 8.10 then move to Jaunty, but unfortunately the PC is located in such a way that the only internet connection it can obtain would be via (my) wireless.

I ran 'lspci -v | less' and the wireless adapter (Belkin Wireless G 1101) shows up, indicating that it's using the kernel module b43-pci-bridge.

If I run ifconfig, on the other hand, it does not show up, and iwconfig only lists eth0 and lo and returns "no wireless extensions" for both.

When right-clicking on the icon, I can see 'Enable wireless' (ticked) when using the .7 kernel (it's not there at all when using the .14 kernel), but 'ifconfig wlan0 up' (also tried 'ifconfig wlan1 up' just in case) returns: 

wlan0: ERROR while getting interface flags: No such device

... for both kernels.

The same thing happened on my laptop at one point, where I had to edit /etc/network/interfaces and remove some entries in /etc/modprobe.d/blacklist. On this computer, however, 'interfaces' already looks like so:

auto lo
iface lo inet loopback

... and I saw nothing suspicious in 'blacklist', plus of course nothing has been added there.

So now I'm begging you guys: suggestions? Ideas? 

Thanks a million!

---

### Post by SuaSwe on 2009-08-22
Please?

---

### Post by SuaSwe on 2009-08-23
*bump* :/

Edit: Is this in the wrong section? Would I be better off moving it to Absolute Beginner Talk?

---

### Post by SuaSwe on 2009-08-23
I would really appreciate help with this as I don't know where to start, even after spending all day yesterday and all night today on Google. Reinstall the wireless card? Upgrade to Jaunty? Format and reinstall with Jaunty?

---

### Post by moore.bryan on 2009-08-23
> **SuaSwe said:**
> 
I ran 'lspci -v | less' and the wireless adapter (Belkin Wireless G 1101) shows up, indicating that it's using the kernel module b43-pci-bridge.

If I run ifconfig, on the other hand, it does not show up, and iwconfig only lists eth0 and lo and returns "no wireless extensions" for both.

When right-clicking on the icon, I can see 'Enable wireless' (ticked) when using the .7 kernel (it's not there at all when using the .14 kernel), but 'ifconfig wlan0 up' (also tried 'ifconfig wlan1 up' just in case) returns: 

wlan0: ERROR while getting interface flags: No such device

Is this the USB network adapter or a built-in network card?
> **SuaSwe said:**
> Please?
*bump* :/
 Edit: Is this in the wrong section? Would I be better off moving it to Absolute Beginner Talk?
I would really appreciate help with this as I don't know where to start, even after spending all day yesterday and all night today on Google. Reinstall the wireless card? Upgrade to Jaunty? Format and reinstall with Jaunty?
Patience, SuaSwe... I know you want to solve the problem yesterday; I've been in the same boat many times, but the forum is charity work by well-meaning volunteers.
Let's work through this with the simple stuff. Like I wrote above, is this the USB adapter? Did you happen upon [this]("http://ubuntuforums.org/showthread.php?t=302357") thread?

---

### Post by SuaSwe on 2009-08-23
I know moore.bryan, I'm being a bit of an impatient bint! I wouldn't worry so much only it's not my computer and I feel partially responsible for its present state. Also, once a thread has gone to page 3 it'll be lost forever without bumping, as I know from many months of frequenting this forum. ;)

It's an onboard card, not USB. The fact that it's listed along with kernel modules seems to suggest (to me at least) that the drivers are installed, but I'm not sure how to proceed from there.

---

### Post by moore.bryan on 2009-08-23
No worries... I've seen the same happen many times.

Could you post your complete lspci, ifconfig, and iwconfig?

---

### Post by SuaSwe on 2009-08-23
I don't have access to the machine at the moment but I can tell you exactly what iwconfig and ifconfig state, as well as a close estimate of lspci.

```

root@dave-desktop:~# iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

```

```

root@dave-desktop:~# ifconfig
eth0      Link encap:Ethernet  HWaddr 00:16:36:92:cd:cd  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:21 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:4 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:240 (240.0 B)  TX bytes:240 (240.0 B)

```

Whereas lspci -v | less (I have yet to run lspci switchlessly) listed the Belkin device under Network Controller, pretty much like so:

09:04.0 Network controller: Belkin something-something rev B 802.11g
        Subsystem: Device 18e8:6194
        Flags: bus master, slow devsel, latency 64, IRQ 22
        Memory at d0108000 (32-bit, non-prefetchable) [size=32K]
        Kernel driver in use: b43-pci-bridge
        Kernel modules: b43

(Above is only an estimate cobbled together from recalled information - although the Kernel driver in use & Kernel modules lines are both verbatim; what I did deduce from it was that it looks to be recognised and installed)

Thanks a whole bunch for your help, by the way. ;)

---

### Post by moore.bryan on 2009-08-23
Hmm... is there *any* way to get the full lspci and other info exact? Do you recall using ndiswrapper?

Oh, and, what kind of desktop/lappie is it?

I also found some interesting reading [here]("http://linuxwireless.org/en/users/Drivers/b43"). If you could run ```
sudo lspci -vnn | grep 14e4
``` that might help...

---

### Post by SuaSwe on 2009-08-23
I'll be able to get the output of lspci shortly, although the more ammunition I have when going over there, the better. :D

I have not used ndiswrapper; it seems that this issue is commonly caused by that app (it was on my laptop, in fact) but this problem occurred immediately following a non-format reinstall of the root/home/swap partitions using a LiveCD; nothing else has been done to it.

And yes, it's a HP Pavillion 7925 desktop, although the wireless card was fitted to it post-purchase.

I'll definitely run the command you linked, although it should be noted that I know the card is at least somewhat supported as it worked fine on the PC before, running first Intrepid then Jaunty.

---

### Post by moore.bryan on 2009-08-23
> **SuaSwe said:**
> I'll be able to get the output of lspci shortly, although the more ammunition I have when going over there, the better. :D
I don't blame you there, at all.
>  I have not used ndiswrapper; it seems that this issue is commonly caused by that app (it was on my laptop, in fact) but this problem occurred immediately following a non-format reinstall of the root/home/swap partitions using a LiveCD; nothing else has been done to it.
I've also had no luck with it, but I thought I'd check just to make sure.
>  And yes, it's a HP Pavillion 7925 desktop, although the wireless card was fitted to it post-purchase.
Do you know the exact card?
>  I'll definitely run the command you linked, although it should be noted that I know the card is at least somewhat supported as it worked fine on the PC before, running first Intrepid then Jaunty.
Thanks... I'm wondering if it's a situation of working with one kernel and not another or maybe some weird module issue.

---

### Post by coolclassic on 2009-08-23
This is very similar to a problem  had. I also had the message "no such device".

My laptop has the Atheros mini card this was not recognised by kubuntu. I tried the madwifi driver but this would not load. 

I tried asking and searching internet forums but with no success.

But what I did find out is the driver "ath5k" is now in the kernal and this sometimes does not work with some cards. With this information I thought that I should blacklist this driver in modprobe.d. I found the driver mentioned in "blacklist-ath_pci.conf".

My internet now works:P. But here's the kick back, I'm still using ath5k go figure:confused:

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Giga-byte Technology Device e913                                                            
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k_pci
        Kernel modules: ath_pci, ath5k

---

### Post by moore.bryan on 2009-08-23
> **coolclassic said:**
> 
But what I did find out is the driver "ath5k" is now in the kernal and this sometimes does not work with some cards. With this information I thought that I should blacklist this driver in modprobe.d. I found the driver mentioned in "blacklist-ath_pci.conf".

My internet now works:P. But here's the kick back, I'm still using ath5k go figure:confused:

Ethernet controller: Atheros Communications Inc. AR242x 802.11abg Wireless PCI Express Adapter (rev 01)
        Subsystem: Giga-byte Technology Device e913                                                            
        Flags: bus master, fast devsel, latency 0, IRQ 18
        Memory at c0200000 (64-bit, non-prefetchable) [size=64K]
        Capabilities: <access denied>
        Kernel driver in use: ath5k_pci
        Kernel modules: ath_pci, ath5k
Sure... you blacklisted the ath_pci (Madwifi) driver, which automatically uses the ath5k one.

---

### Post by SuaSwe on 2009-08-23
Hmm, that's interesting! Will have a look at that; I did check the blacklist file as an identical problem on my laptop was caused by me having played around in there. I've not looked in blacklist-ath_pci.conf so I'll definitely do that.

I too think it's a kernel problem as both the volume and mouse play up on the x.14 kernel, but not x.7 (both of these show up in the GRUB menu - there are in fact two entries of the x.14 one for reasons unknown). The wireless, sadly, works on neither. 

Do you guys know if I'd be safe to upgrade to Jaunty without having updated everything on Intrepid first? Alternatively, is there a way for me to upgrade Intrepid's kernel without an internet connection? I've had a read-around on this but instructions are conflicting and confusing.

---

### Post by moore.bryan on 2009-08-23
You *could* just download the latest mainline kernel available, with headers, and install that. 
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-headers-2.6.31-020631rc7_2.6.31-020631rc7_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31-rc7/linux-headers-2.6.31-020631rc7_2.6.31-020631rc7_all.deb")
[http://kernel.ubuntu.com/~kernel-ppa/mainline/v2.6.31-rc7/linux-image-2.6.31-020631rc7-generic_2.6.31-020631rc7_i386.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v2.6.31-rc7/linux-image-2.6.31-020631rc7-generic_2.6.31-020631rc7_i386.deb")

I *would not* upgrade selectively... all-or-nothing is the better choice.

---

### Post by SuaSwe on 2009-08-23
> 
I would not upgrade selectively... all-or-nothing is the better choice.


Do you mean that upgrading just the kernel and headers is not a good idea? Basically, I wouldn't know where to start with fetching and installing ALL Intrepid updates. Would upgrading to Jaunty be better? Or reinstalling using Jaunty?

---

### Post by moore.bryan on 2009-08-23
> **SuaSwe said:**
> Do you mean that upgrading just the kernel and headers is not a good idea?
Upgrading the kernel & headers would be just fine... I meant picking and choosing different programs isn't usually a good idea.
> Would upgrading to Jaunty be better? Or reinstalling using Jaunty?
If it's an option, I would completely reinstall using the latest Jaunty CD.

---

### Post by SuaSwe on 2009-08-23
"Option" may be a strong word - needs must, but if I'll save myself a lot of copy-paste time later if I can avoid having to reinstall!

Sorry for being a bit thick but how do I install the headers you linked above? Will try that first then reinstall if all else fails.

---

### Post by moore.bryan on 2009-08-23
If possible, you could download the debs onto a usb thumbdrive, head-over to the other computer, fire-up a terminal, cd to the usb thumbdrive, and ```
sudo dpkg -i linux*.deb
```

That *should *take care of things.

---

### Post by SuaSwe on 2009-08-23
Definitely sounds like something I can do! Will try it tomorrow, probably, and let you know what happened. :)

---

### Post by moore.bryan on 2009-08-23
Keep us informed...

---

### Post by SuaSwe on 2009-08-24
Here I am, back to keep you guys informed!

Good news: it's working. I never got the chance to try the kernel/header upgrades as my neighbour wiped and reinstalled Intrepid with my trusty LiveCD (away from my watchful eye he installed it with only swap and root partitions, which I hope will not cause issues), then dragged the computer over here where we connected it via ethernet (which worked fine), upgraded Intrepid fully (to be on the safe side) then upgraded to Jaunty. It took a good hour and a half but at the end of it, once Jaunty was installed, the Hardware Drivers manager took note of the wireless card and prompted the installation of its driver, following which it worked like a charm.

I realised earlier that wireless was never actually tested on Intrepid on that machine as the hard drive had been moved over from a Dell with Jaunty already installed, so in the end it looks like perhaps Intrepid didn't have support for the card. 

I thought I'd paste in the lspci here just in case other people with the same problem ever find themselves scouring Google for keywords much like I was doing over the weekend. :)

```

root@desktop:~# lspci
00:00.0 Host bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133] (rev 81)
00:01.0 PCI bridge: VIA Technologies, Inc. VT8363/8365 [KT133/KM133 AGP]
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:07.5 Multimedia audio controller: VIA Technologies, Inc. VT82C686 AC97 Audio Controller (rev 50)
00:0d.0 Network controller: Broadcom Corporation BCM4306 802.11b/g Wireless LAN Controller (rev 03)

```

Anyway, problem solved and all is calm once more!

---

### Post by moore.bryan on 2009-08-25
> **SuaSwe said:**
> I realised earlier that wireless was never actually tested on Intrepid on that machine as the hard drive had been moved over from a Dell with Jaunty already installed, so in the end it looks like perhaps Intrepid didn't have support for the card. 

Well, that would have been some useful information! ;-)

Congrats on the working Ubuntu...

---

