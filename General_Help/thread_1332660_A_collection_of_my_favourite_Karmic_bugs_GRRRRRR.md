---
title: "A collection of my favourite Karmic bugs GRRRRRR"
date: 2009-11-20
forum: General Help
---

### Post by slumbergod on 2009-11-20
I don't know if all of these have been filed as bug reports or not; I tried to report a couple and just wasn't able to work out how to post a new one. Instead, maybe someone who reads this has found a workaround. I certainly haven't. I have search high and low without luck.

1. WICD - when I get disconnected from a wireless network, I have to reboot my laptop to reconnect. Killing all the wicd processes and restarting them doesn't work as it did in Jaunty.

[SOLVED] instead of manually killing and restarting the wicd daemon and client, I instead have to stop and restart the wireless modules. 
# modprobe iwl3945
# modprobe iwlcore
# modprobe mac80211
then in reverse to restart them. After that I connect instantly. This probably would have improved my Jaunty experience too had I known it then!

2. Gnome-Help (yelp) - I had to delete the gnome-help file because everytime I accidentally knocked the F1 button and a help window popped up which then completely locked up my machine - forced reboot required! I never use help but it concerns me that something so important as this has teh potential to lock up a machine - perhaps not so good for someone new to ubuntu.

3. Gnomebaker - in Jaunty, it used to detect my DVD writer's burnfree ability. In Karmic it doesn't.

4. Deluge - now requires as many as 10 manual restarts before the GUI loads. In Jaunty it was always flakey but not as bad as it is now.

If I could resolve these issues I'd actually have to say Karmic was pretty good. But these seemingly minor issues bug the hell out of me. Perhaps you've got some of your own? Twice a day I check for Karmic updates but I haven't seen any come through for a week or so now.

---

### Post by P4man on 2009-11-20
those are not minor issue (nor are they common) and more likely than not, most of them  are related.

Lets start by checking you have the right kernel. Whats the output of
```
uname -a
```

---

### Post by slumbergod on 2009-11-20
Hi, thanks:

Linux slumbergod-laptop 2.6.31-15-generic #50-Ubuntu SMP Tue Nov 10 14:54:29 UTC 2009 i686 GNU/Linux

That's the correct kernel isn't it?

---

### Post by P4man on 2009-11-20
yeah its correct. Bummer.
next, can you post your logfiles?

/var/log/messages
/var/log/syslog

Also what machine is this? Can you post output of

```
lspci
```

---

### Post by slumbergod on 2009-11-20
lspci:
-----------------------------------------------------------------------
00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 03)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 03)
00:1c.2 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 3 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f3)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 03)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 03)
05:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5787M Gigabit Ethernet PCI Express (rev 02)
06:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
07:00.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
07:00.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
07:00.2 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
07:00.3 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
________________________________________________________

How do you post or attach the logs when they are so big?

---

### Post by P4man on 2009-11-20
zip/rar/arj them, should be able to upload m then. If not upload it to [http://www.mediafire.com/](http://www.mediafire.com/) or something.

---

### Post by slumbergod on 2009-11-20
Ah, yes, you are right...they squash considerably.

---

### Post by slumbergod on 2009-11-20
Actually, you have me thinking now. Perhaps I should just go to the PPA for the Ubuntu kernel team and grab the stable one I was using in Jaunty. I found Jaunty a total mess with the intel regressions so I jumped ahead to the 2.6.31 kernel builds and that was a huge improvement. It could be that the kernel that comes with Ubuntu just isn't good with my hardware.

Unless you see anything weird but obvious in my logs....?

---

### Post by Giblet5 on 2009-11-20
I thought the -15 kernel was held back...

It's not in my updates and I'm on -14.

Why not try booting your previous (-14) kernel and see if things look happier?

It should be the third entry in Grub.

---

### Post by P4man on 2009-11-20
dont use the jaunty kernel, but you could try the -14.
I see kernel oopses that I think are caused by the wifi driver which is in the backports. Have you enabled backports and proposed repositories, and if so, for any particular reason?

---

### Post by slumbergod on 2009-11-20
Ok, I will boot with the -14 release and try that for a while. Failing that, I just grabbed the latest 2.6.31 release from the kernel team.

---

### Post by slumbergod on 2009-11-20
I've always had better luck in the previous Ubuntu releases with Proposed and Backports. That is why I normally have them enabled...just to grab fixes faster. I can try rolling back to the current versions and see what happens.

---

### Post by Giblet5 on 2009-11-20
It's a good guess, as guesses go, but remember that by using a kernel other than the one that is sprinkled with the Ubuntu team's official blessings can go either way: miracle or big mistake.

---

### Post by P4man on 2009-11-20
Backports and proposed are good if you're having problems. But they are not stable for a reason, so always try stable releases first and only enable them if there is any chance of it fixing bugs rather than just introducing new ones.

---

### Post by slumbergod on 2009-11-20
Right rebooting to kernel -14 now. Ummmm, I have no idea which packages might have been updated from proposed or backports. Synaptic doesn't have a simple way of identifying which packages are updated to newer versions than the standard, non-proposed/backports versions does it?

---

### Post by Giblet5 on 2009-11-20
I don't see a way to filter the installed packages that way...

---

### Post by Manyette on 2009-11-20
Re: Kernel.  I am running 9.10 and have the latest updates, and my kernel is 2.6.31-14. Am I missing something here?

---

### Post by florus on 2009-11-20
> **Manyette said:**
> Re: Kernel.  I am running 9.10 and have the latest updates, and my kernel is 2.6.31-14. Am I missing something here?

I don't think so. Both my Karmic fresh installs use 2.6.31-14

---

### Post by slumbergod on 2009-11-20
No Manyette, you are fine. I have had a few weird issues with Karmic. The others were suggesting it could be related to me using bleeding-edge kernels and drivers. -14 is the kernel you should have unless you enable the proposed repo.

---

### Post by slumbergod on 2009-11-20
Still no Burnfree tick box in Gnomebaker even using kernel 2.6.31-14. 

I am sure it was there in Jaunty. Does anyone have gnomebaker installed? do you get the checkbox when you click BURN and the final dialog box pops up?

---

### Post by slumbergod on 2009-11-20
Actually, reverting to the 2.6.31-14 kernel has reintroduced another annoying bug...my system fan is now in overdrive mode. It was better with -15.

---

