---
title: "How is hardware detected? (Broadcom 4311 Wireless Issues)"
date: 2010-05-12
forum: General Help
---

### Post by adamis on 2010-05-12
I have a laptop that has a BCM4311 wireless card in it. Things were working fine for quite a while. One day my mother turned it on and the wireless wasn't working. I initially thought it was a software problem but after running lspci and lshw I discovered that the broadcom card is not even mentioned in the output.

My question is, if this is a software issue such as the driver not loading would the card still show up with either of these commands? Since the card is not showing up I was assuming that it was bad but it seems odd to me that the thing would work for a couple of years and then magically die. 

This laptop was running 9.10 when the wireless card disappeared. Since I was doing work on the laptop I upgraded to 10.04 but no changes.

I've also looked through DMESG to see if there was anything mentioned about the Broadcom card and nothing showed up as well. The laptop is a Presario F500 with the Nvidia chipset and Broadcom 4311 wireless card. I have also tried running a liveCD and it still came up empty. 

So my specific question is, does a driver need to be loaded for lspci and lshw to show a card or does the hardware just have to be plugged in? Also are there any other commands that might help me figure this out.

---

### Post by prshah on 2010-05-12
> **adamis said:**
> after running lspci and lshw I discovered that the broadcom card is not even mentioned in the output.

Sometimes, the card is an (internal) usb card; it will not be mentioned in lspci and lshw; check lsusb.

If lsusb does not mention it either, then I guess you're right, the card is broken.

Neither lspci, lshw nor lsusb require a driver to be loaded, to report the existence of hardware; but be aware that some (cheapo) manufacturers will simply externally rebrand the hardware, which means that the lspci/lsusb reports can seem unrelated to the brand in question.

---

### Post by Martin Marshalek on 2010-05-18
I seem to be in the same proverbial boat as you adamis. I have the Presario F730US with the same wireless chip you seem to have and it has not shown up. Initially I thought it was an issue caused by Suspend in Lucid as that was when it failed for me yet you seem to have had the problem with Karmic as well. I too have checked lspci, lshw, and dmesg to no avail. I reinstalled, installed Fedora, and reinstalled Windows with no luck. It came back for about 3 days only to stop working afterwards. I even opened up the computer and removed the card and reinserted it yet nothing worked. I can only conclude that this is simply that the card itself has a defect and is faulty.

There is a chance you can fix this though. I have yet to attempt this yet I probably will within the next two weeks. The card is extremely simple to replace. All you need to do, assuming the F500 is similar to the F700, is remove the bottom door, unscrew the two screws next to the rectangular chip to the right, disconnect the two wires, and it should just slide out. Replacements go from 30-100 USD so you can find a quality for your purposes.

---

