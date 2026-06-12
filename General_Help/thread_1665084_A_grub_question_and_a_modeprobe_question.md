---
title: "A grub question and a modeprobe question"
date: 2011-01-11
forum: General Help
---

### Post by bdemers on 2011-01-11
Here is a quote taken from an earlier posting regarding a sun 501-5406 quad nic card using the sunhme driver.  What's happening here is the sunhme and the boot procedure not being nice in the sandbox.  With every reboot 4 new eth#'s get added to the 70-persistent file.  Ugly!:

[QUOTE]There's just two simple steps: 

First, add blacklist=sunhme to the end of whichever kernel= line you boot from in /boot/grub/menu.lst. Heck, add it to every kernel line. 

Next, specify your own mac address by creating /etc/modprobe.d/sunhme with contents: 

```
options sunhme macaddr=0x00,0x00,0x00,0x00,0x00,0x01
```
/QUOTE]

My questions

      1. I am using grub2 and in the /etc/default/grub file I don't see a good place to put the blacklist command.  Where should it go?


      2. I would like to use specific mac addresses ( I have the actual hardware addresses). How should I format the code to support the mac addresses I want to use?  I can't find any docs on using the sunhme macaddr .  There isn't a man for sunhme.  

It appears that macaddr=0x00,0x00,0x00,0x00,0x00,0x01 is the 6 byte mac address for the first port.  If I enter the low value here the system may increment for the other 3.  That will be what I want. But I gotta get that blacklist in first.

By the way, FreeBSD returns the hardware macs just fine. This issue has been around at least since 1997. I don't look for a rewrite on the driver, this simple workaround is fine by me.  Issue now is the grub to grub2 switch.

---

### Post by mikewhatever on 2011-01-11
> **bdemers said:**
> ...

      1. I am using grub2 and in the /etc/default/grub file I don't see a good place to put the blacklist command.  Where should it go?

...

Should probably go to the end of the 'GRUB_CMDLINE_LINUX=' line.

---

### Post by bdemers on 2011-01-11
Well, I put it in, and it didn't freeze up the boot, which I have done many times with other attempts.  Unfortunately the address didn't get altered to what I wanted.  

Too many possibilities as to why.  Any way to test for the blacklist entry being correct?

I am tempted to go back to doing a 8.04 install and see if the provided algorithm actually works with grub1.

---

