---
title: "How to get an Internal multi-card reader working?"
date: 2009-11-30
forum: General Help
---

### Post by Vyrlokar on 2009-11-30
I just decided to switch my desktop to Ubuntu 9.10 (My netbook has been running on UNR for a while) and everything was a breeze, except that I can't get my internal card reader working (It's one of those multi-card readers that connects to the internal USB port). Any ideas? Right now, the led doesn't even light up when I insert a card.

The reader doesn't seem to be listed on lspci (I already tried that)

---

### Post by spvo on 2009-11-30
I have a similar multi-card reader.  To get mine working I had to plug it into the motherboard, with a card in the reader, while the computer was booted up.  The flash card immediately popped up on my desktop.

Also, I only had to plug it in that way once.  It has continued to work correctly ever since.

---

### Post by tiger2wander on 2009-12-07
I have same problem with you, Only way can make it works for me is place the card in the card reader slot before boot up computer then Ubuntu will recognize Card Reader hardware and insert driver for it. BTW you will have card reader working fine for that boot time :)

---

### Post by Vyrlokar on 2009-12-11
Well, so far, no luck at getting that piece of crap working.
I haven't tried opening the computer, and plugging the reader after it has started though.

Here's the output of lsusb
> Bus 001 Device 004: ID 0c45:627b Microdia PC Camera (SN9C201 + OV7660)
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 002 Device 005: ID 0d8c:5000 C-Media Electronics, Inc. Mass Storage Controller
Bus 002 Device 004: ID 0e8f:1140 GreenAsia Inc. 
Bus 002 Device 003: ID 0a12:0001 Cambridge Silicon Radio, Ltd Bluetooth Dongle (HCI mode)
Bus 002 Device 002: ID 062a:0000 Creative Labs Optical mouse
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


It's device 5 on bus 2. Any ideas on how to make it work?

---

### Post by soulsource on 2009-12-11
Just a guess: You might try to tell your system to scan all SCSI LUN's. I'm sorry I can't tell you how, since I haven't played around with grub2 and therefore don't know how to pass options to the kernel...

I think the kernel parameter would be
scsi_reportluns2=1
but better check that, for I'm not sure.
I also don't really think it will help, since I thought that would already be turned on in Ubuntu by default....

Here's another discussion on a topic that might be related, yet it's for slackware linux:
[http://fixunix.com/slackware/518681-sony-ericsson-k850i-support.html](http://fixunix.com/slackware/518681-sony-ericsson-k850i-support.html)

---

