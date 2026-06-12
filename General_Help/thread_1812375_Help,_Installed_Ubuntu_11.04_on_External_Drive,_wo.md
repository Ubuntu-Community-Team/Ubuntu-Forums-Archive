---
title: "Help, Installed Ubuntu 11.04 on External Drive, won't go past blinking cursor"
date: 2011-07-26
forum: General Help
---

### Post by ckirkp79 on 2011-07-26
Hi, I am not nec new to Ubuntu but I am new to installing it on an External Hard Drive. So here is what happened: I made a live usb with my flash drive put both in and booted off the live usb (with no problem), I went into install and first I tried partitioning it myself and that didn't work so I used the Guided Partitioning and wanted it to use my whole 500gb External Hard Drive.

I don't know if brand matters but it's a Toshiba Booklet external drive. Install went perfect, no errors or anything...so I rebooted and went into bios, set it to boot off Toshiba drive this time and it went to a black screen with a blinking cursor. When I hold the shift key I get: Grub Loading..

Strange thing is..I know linux works on my external because I tried pclinuxos on it and it booted into that just fine. But when it boils down to Ubuntu 10.10, 11.04 Amd64, or i386 it won't boot past black screen. I even tried Linux Mint 11 and it was no go.

I really want to use Ubuntu on my external. I did everything correctly-installed the bootloader to /sdb. Can anyone help me, I've been at this for a week now.

TIA

---

### Post by scouser73 on 2011-07-26
I'm sure I've read that if you're installing to an external HDD that you need to disconnect the internal HDD for it to be recognised.

---

### Post by ckirkp79 on 2011-07-26
I guess I could try that...I have read that as well but I was sort of hoping not to break open my laptop. I will try anything...I just want it to work because I really dislike windows 7 but I gotta keep it on there because I am not the only one who uses the laptop:( Thanks for your response...I hope other people put their input in as well in case this doesn't work...I'll update this when I give it a whirl.

> **scouser73 said:**
> I'm sure I've read that if you're installing to an external HDD that you need to disconnect the internal HDD for it to be recognised.

---

### Post by Mark Phelps on 2011-07-26
It's fairly standard for a new install to write GRUB to the "first" drive it sees -- and in the case where there are both an internal drive and an external drive, the internal is often the "first".

If the PC boots with the internal drive connected, that's because GRUB exists there.

What often works is that you do the following:
1) Remove the internal drive
2) Connect up the external drive
3) Reinstall GRUB.  Since there is only one drive now, it will install to the external drive automatically.

Then, when you reconnect your internal drive, you will need to use the BIOS to determine which to boot -- since they are both bootable now.

---

### Post by ckirkp79 on 2011-07-26
Thank you for your response, however I don't know if it mattered or not, when I was in process of installing...right before actually installing-there was an advance button-I clicked that and told it to install bootloader to my external drive which was sdb-I didn't install it to any partition within the external-and it did not affect the install of windows either...

I will def try pulling the internal out-it seems that is the last option I really have left. I've googled and googled for what seems like eternity and see everyone having successful external installs-but my case it's been trouble.


> **Mark Phelps said:**
> It's fairly standard for a new install to write GRUB to the "first" drive it sees -- and in the case where there are both an internal drive and an external drive, the internal is often the "first".

If the PC boots with the internal drive connected, that's because GRUB exists there.

What often works is that you do the following:
1) Remove the internal drive
2) Connect up the external drive
3) Reinstall GRUB.  Since there is only one drive now, it will install to the external drive automatically.

Then, when you reconnect your internal drive, you will need to use the BIOS to determine which to boot -- since they are both bootable now.

---

### Post by ckirkp79 on 2011-07-26
Ok, so I took my internal out, and reinstalled Ubuntu on my external...put my internal back in and I am back to square one-blinking cursor on black screen. What am I doing wrong? It's literally driving me bonkers. I thought I had it this time but I guess I'm going to just put ubuntu on my other spare drive and just switch hard drives in and out until I can get this figured out. 

Is there any possible way to clone an installation onto an external? I was thinking maybe install ubuntu on my other 500gb internal drive and then cloning it to the external? I don't know if it's possible or what I would poss use..but this is a big mess and I love ubuntu lol.

---

### Post by ddastoor on 2011-07-26
a) ok u could have ur internal drive as: /dev/sda (im assuming)
b) ubuntu live installer drive (flash usb): /dev/sdb
c) the target drive (external USB HDD):/dev/sdc

1) u boot off b) to start the installation process
2) when installing u chose c) as ur target, right ?
3) at some point (if i remember correctly) set he boot loader to load to the target drive c) (not default a) )
4) NOW go ahead and boot from target drive c) using the bios seq.


can u try this ? well.. just a hunch from the symptoms...

---

### Post by ckirkp79 on 2011-07-26
Yeah to that extent...sda is internal drive
sdb is the external drive and sdc is my usb flash drive

So in a switch I boot off of sdc and install onto sdb. and yes the bootloader is attached to sdb as well. I have tried to boot after all that and it's the lovely black screen with cursor and hitting shift during boot shows: grub loading. (that's exactly what it shows)

I'm getting ready to try a virtual box install of ubuntu onto my external since my other spare internal is fried. I'll spill out some specs and maybe it's just the laptop I am using...
  **EDIT** I am under ubuntu in workstation and it's showing my external as what you said sdc...guess I'm going to try and reinstall again...maybe I missed something but who knows.

Toshiba Satellite L675D-S7049
Amd Turion X2 2.4ghz Dual Core
500gb Samsung Internal drive
4gb DDR3 Mem
ATI Radeon Mobility HD 4250 


> **ddastoor said:**
> a) ok u could have ur internal drive as: /dev/sda (im assuming)
b) ubuntu live installer drive (flash usb): /dev/sdb
c) the target drive (external USB HDD):/dev/sdc

1) u boot off b) to start the installation process
2) when installing u chose c) as ur target, right ?
3) at some point (if i remember correctly) set he boot loader to load to the target drive c) (not default a) )
4) NOW go ahead and boot from target drive c) using the bios seq.


can u try this ? well.. just a hunch from the symptoms...

---

### Post by ckirkp79 on 2011-07-26
I'm still stuck. I thought at one point when I tried to reinstall grub that I had actually got it working...so when I rebooted it actually brought me to the grub loader I think...with >grub (could be wrong on where that arrow is pointing) and I couldn't figure out where to go from there. Tried using terminal to see if I could get into safe mode or low graphics mode and didn't work.

I'm scratching my head on this one and going to see if I can install pclinuxos with ubuntu and see if the bootloader from pclinuxos will allow me to boot into ubuntu that way. Any other suggestions??

---

### Post by 1234blizzard on 2011-07-26
Maybe you should try to install ubuntu through a cd. When I got mine working, I didn't need to unplug the internal hard drive. I also had grub installed onto the external.

---

### Post by ckirkp79 on 2011-07-26
I had initially tried to install via dvd since we don't have cdr's available...when it failed-that's when I decided to do usb route being i have plenty of microsd cards and my adapter to boot.

But thanks for you help...one day i'll get it rolling and hopefully when someone runs into the same situation as me, i can help them out.
> **1234blizzard said:**
> Maybe you should try to install ubuntu through a cd. When I got mine working, I didn't need to unplug the internal hard drive. I also had grub installed onto the external.

---

### Post by ddastoor on 2011-07-27
> So in a switch I boot off of sdc and install onto sdb. and yes the bootloader is attached to sdb as well. 


im assuming that the bootloader is attached to the MBR of sdb (/dev/sdb), not /dev/sdb1, right ??

---

### Post by ckirkp79 on 2011-07-27
Yeah the bootloader was added to sdb...and for just giggles I tried to install it onto sdb1...and it was a no go. I have gave up for the time being as I have been working and reading on this for too long now..think I'm going to do the dual boot..and just install it alongside my windows 7. 

What's weird is my 2gb usb flash drive boots the live cd up perfectly-no issues whatsoever and it was the drive listed as sdc..whereas in virtual machine it said my 500gb drive was sdc instead...too much to think about now. 

But thanks everyone for ideas and suggestions...this forum have been great...

> **ddastoor said:**
> im assuming that the bootloader is attached to the MBR of sdb (/dev/sdb), not /dev/sdb1, right ??

---

### Post by cbowman57 on 2011-07-27
Is grub booting using UUID or is it /dev/sd*?

My thought is that when you are doing the install it's reading the flash drive, then you reboot and it shuffles the drive letters around.

Have you tried editing the grub boot line or doing a sudo blkid to verify the UUID if grub used them for the installation?

---

### Post by ckirkp79 on 2011-07-27
I believe grub has to be booting /dev/sdb, but you just gave me something to try before I was going to install this on my internal. I'm going to try burning a disk again...and see what happens after I install it on the external. If no joy then I am going to see about editing the UUID maybe that is what is missing..that would be awesome.

> **cbowman57 said:**
> Is grub booting using UUID or is it /dev/sd*?

My thought is that when you are doing the install it's reading the flash drive, then you reboot and it shuffles the drive letters around.

Have you tried editing the grub boot line or doing a sudo blkid to verify the UUID if grub used them for the installation?

---

### Post by ddastoor on 2011-07-27
if /dev/sda is switched to sdb or sdc, then im assuming u'll smiply boot into the swithed drive, so wither ur internal drive or ur flash live ubuntu install (if it's still in the slot while booting)... right ?

---

### Post by ckirkp79 on 2011-07-27
when i was in live cd sda was my internal drive, sdb was my 500gb external and sdc was my 2gb flash drive. I also kept the 500gb external drive plugged into the same usb slot after I installed...and just removed the live usb when it told me to or after I realized the bios was booting back up after restart.

I just went ahead and caved in: installed ubuntu onto my internal and am happy even if it's taking up half my drive...the only thing I haven't tried to do with the external installation is reburn a dvd and see if it works pulling the internal out. If I give it a swing..i'll be sure to add what happens here in case someone stumbles upon this thread.

But thanks for your help...I just got aggravated with trying and failing so many times and I knew it would install on my internal as this is a newish laptop (2010 lol).

> **ddastoor said:**
> if /dev/sda is switched to sdb or sdc, then im assuming u'll smiply boot into the swithed drive, so wither ur internal drive or ur flash live ubuntu install (if it's still in the slot while booting)... right ?

---

