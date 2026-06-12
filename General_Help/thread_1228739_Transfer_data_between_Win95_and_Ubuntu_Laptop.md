---
title: "Transfer data between Win95 and Ubuntu Laptop"
date: 2009-08-01
forum: General Help
---

### Post by oake on 2009-08-01
I would like to get  large amounts of data off a old Win95 machine onto a Ubuntu laptop
 

 of the order of tens of Meg, so thinking
 - ~laplink equivalent down the serial port, that works between species of operating system
 - zip it up and zmodem it across, but not found reasonable/GUI tx & rx zmodem on Ubuntu??
 

 want to avoid  
 - upsetting the network setup as re-configuring is more like witchcraft rather than science
 - extracting the hard disk and experimenting with a USB ide adaptor
 - floppy disk (ie chunks or zip chaining) via another computer and USB stick
 

 I'm a bit surprised that it's such a problem

---

### Post by lisati on 2009-08-01
If your win95 machine has an ethernet card (or you are able to install one) then using samba might be an option. I successfully connected a win98 machine to Ubuntu after I installed an ethernet card.

---

### Post by Rob_H on 2009-08-01
> **oake said:**
> 
 - ~laplink equivalent down the serial port, that works between species of operating system
 - zip it up and zmodem it across, but not found reasonable/GUI tx & rx zmodem on Ubuntu??


Wow, this brings back memories. This could have been a post straight out of the nineties. :-D But seriously, here in 2009, your best bet is Ethernet if it's available. Ubuntu can connect to Windows shares via Samba. If that's not an option, a USB thumb drive should work, as it'll easily hold several GBs. No chunking required.

---

### Post by oake on 2009-08-01
> a USB thumb drive should work
bit of a problem as this machine does not have USB
I guess in it's day USB could be added, but I think it would be risky now as
any hardware isn't going to come with relevant drivers

 > I successfully connected..
Your phrasing implies it was not easy, which I infer from other folks exploits

I'm just hoping a serial based solution will emerge

---

### Post by lisati on 2009-08-01
> **oake said:**
> 

 > I successfully connected..
Your phrasing implies it was not easy, which I infer from other folks exploits

I'm just hoping a serial based solution will emerge

I have no experience using the serial port that might be relevant here. 

What I did was to open up my win98 box, replace the modem with an ethernet card (about 10-15 minutes work max, only two PCI slots in the machine, originally they held the modem and the sound card), install the relevant drivers and networking software (about 10-15 minutes max, I had to look up some of it in the Win98 book that came with the machine, looking things up slowed things down a bit) and then install and configure samba on the Ubuntu box.

---

### Post by MaxIBoy on 2009-08-01
It really all depends on whether the Win95 machine is a laptop. If it's a laptop, it's going to be more difficult to open up and install more parts. 

Assuming for a moment that it's not a laptop, you can easily buy an old win95-era PCI or ISA ethernet card for less than a dollar at your nearest electronics junk store. Slap it in, install the drivers, and you're in business (assuming you can coax win95 to share files over the network.) Just bring the computer into said electronics store so you can try it out in the shop.

A probably-even-easier option is to get an external hard drive enclosure. Slap the hard drive into the enclosure, you've got an instant external USB hard drive with all your data on it!

---

### Post by lyfenda on 2009-08-01
MAXLBOY you just completely ditched my thread dude.

---

