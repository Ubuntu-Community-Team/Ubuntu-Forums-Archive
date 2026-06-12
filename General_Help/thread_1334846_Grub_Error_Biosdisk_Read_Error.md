---
title: "Grub Error: Biosdisk Read Error"
date: 2009-11-22
forum: General Help
---

### Post by ncweber on 2009-11-22
Greetings everyone.  I am hoping you good folks can help me out of a dodgy situation.  I've been running Ubuntu Netbook Remix 9.10 on an Acer Aspire One AOA110 netbook with an 8GB SSD.  It's been running beautifully so far.  That is until today.

I had gone to a birthday party and taken many digital pictures.  When I came home, I booted up the Acer and transfered the pics using F-Spot.  Then, I shut down the machine, and went out to dinner.  Upon coming back, I went to boot up the Acer again, and I am getting the following message.

Grub loading.

error: biosdisk read error
  Failed to boot default entries.
Press any key to continue...

Pressing a key merely repeats the error.  I've tried searching for a solution here and other places, but all the other references to this problem deal with dual booting into Windows.  I just have the UNR on this machine.  Any help would be greatly appreciated.  Thank you.

---

### Post by ncweber on 2009-11-26
Hello?  Anyone there?

---

### Post by KrisDouglas on 2009-11-30
Confirming this, its died for me too, i just get dropped to the grub rescue command line. quite frustrating.

---

### Post by boot_sectorz on 2009-12-11
Ok this ubuntu has driven me into unknown roads! I have bugs after bugs. Is there a way to solve this for my dual-boot, at least the doze OS is boot but i have no access to my ubuntu partition

---

### Post by wtfbrb on 2010-01-03
I have the same issue on the same AOA110.  I tried upgrading to the new bios, I nearly had it once and that required first booting into live usb then installing from there.  But after updating it went back to the grub command line.  Any help on this issue would be appreciated.

---

### Post by jampr on 2010-01-11
Hi at all,
 
for me the same. I have a jetway mini-itx board with an ide-to-cf adapter with an 2 gb cf card.
after an upgrade i only see grub prompt with the message '**Grub Error: Biosdisk Read Error**'
I tried a 8 gb cf card with a complete new installation of ubuntu desktop and server. all of them throw the same error message.
 
I hope somebody can give me a solution how to correct  this issue.
 
thanks in advance 
jampr

---

### Post by decoherence on 2010-01-30
Bump. Problem here as well. Gateway LT3100

---

### Post by mdurkin on 2010-01-31
I also have a jetway mini-itx (NC62 - amd) with CF to IDE adaptor! Funny co-incidence this! Same error. Can't boot. I updated to the latest firmware and still no luck.
Installing Ubuntu 9.10 64bit from the alternate install CD. root is on /dev/sde1 and I watched grub install the MBR on /dev/sde which is my CF card so should be correct.
I'm going to have another go with legacy grub and see if that works. If it does that's fine - I don't need any of the new grub 2 features...
will report back.

---

### Post by mdurkin on 2010-01-31
OK - I've got mine working - here's how.
I used the alternate install CD in expert mode so I had full control.
I created a small /boot partition (200MB) as an ext3 partition, then used the rest of the CF space as ext4 for / (root).
grub2 now loads with no problem at all. No idea what the bug is, but the exact same CF card and adaptor worked fine on my old intel atom motherboard...

I'm not sure how much of this can be done from the graphical installer, but I always work with the alternate installer as it gives more control of disk partitions (and I have a raid 5 setup I didn't mention for /home).

Hope that helps,
Matt

---

### Post by samuraibrian on 2010-03-17
Just to keep this alive... I too am suffering from this one. My setup:
Intel D510MO (Atom CPU, NM10 chipset) Mini-ITX mobo; 2GB RAM; SATA Port 1 is SATA <> Compact Flash adaptor; SATA Port 2 is 320GB HDD.
For OS, am using (have tried...) both Xubuntu 9.10 Live CD installer, and Netbook Remix 9.10 Live CD installer - in both cases, the "Live CD" was actually a 4GB USB pen drive.

Have tried to install to:
- 4GB Sandisk Ultra II (max. MWDMA2)
- 8GB Lexar 233 Professional (max. UDMA/66)
- 8GB Transcend 133 (max. UDMA/66)

Installation to 4GB Sandisk absolutely fine - no deviation from the "Install to Hard Disk" wizard was required. (Although subsequently successfully setup the 320GB HDD as /home.)
Installation to both 8GB CF cards essentially has proved impossible! Writing this after 6 days of (part-time!) googling... What I learned:

- Booting from "Live CD" when the 8GB CFs were plugged-in was incredibly slow. Boot logs showed repeated errors as libata tried to configue the CF card. After much experimentation, overcame this by adding "libata.force=1:mwdma2" (any of the pio settings worked, too) to kernel load command line.
- From there, I was able to "Install to Hard Disk" to either of the 8GB cards. Everything (including the boot / grub stuff) looked just fine - I was able to add the "libata.force=..." stuff to /dev/sda's grub.cfg, via the proscribed method - [https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202](https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202) (Method 3). But, when I tried to boot from them, I ended-up at the "grub rescue" prompt, via the "error: biosdisk read error" message.
- From "grub rescue", I could not really do anything useful... "ls" (eventually) returns to the rescue prompt, with no partitions listed. Trying to generate a simple, appropriate boot setup ("set dev=/dev/sda"; "set prefix=(hd0,1)/boot/grub"; "set root=(hd0)"; "insmod normal") got me nowhere - just returned to rescue prompt with a "error: no such partition" message. "ls" then also (eventually) returns with the same error...
- Tried **loads** of stuff since then, none of which has got me beyond booting to the grub rescue prompt. (Can still boot OK with "Live CD" USB stick, and the "libata.force=... " line. Can still boot just fine with the 4GB Sandisk card.)

Don't think it's a hardware / BIOS problem, otherwise wouldn't be able to boot using Live CD + 8GB CF card + libata.force=.... It appears that libata HAS to be configured to support UDMA-capable CF cards. That configuration has to be done when the kernel is loaded. Before that, Grub itself initialises OK, but cannot see the partitions on the CF card, because libata has yet to load... See no way out of this.

</wit's_end>

Any wacky ideas, anybody?

---

