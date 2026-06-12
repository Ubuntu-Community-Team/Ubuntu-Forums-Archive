---
title: "Notebook died. Replacement recommendations?"
date: 2006-05-30
forum: General Help
---

### Post by drfox on 2006-05-30
My 3-year old notebook hard drive just died. I'm looking for notebook suggestions. It seems my choices are AMD64, Intel single or dual core. 
My current notebook is a Centrino, so I don't want to "downgrade" to a Celeron M (do I?) 

Thanks.

Larry

---

### Post by nwgray on 2006-05-30
It really comes down to what your usage of the notebook is. Wal-Mart has several decent laptops for around $700. They would be great for surfing the web, word processing, etc. However, Dell also has some great ones for less than $900. What's your budget, needs, etc.?

Nathan

---

### Post by mostwanted on 2006-05-30
I'm getting an AUS v6j which is powerful, but mobile laptop (between 2.5 and 3 cm thick) sporting a Core Duo, Nvidia graphc, Intel wifi and a nice brushed aluminum design with a brownish tint even!

This is not an advertisement, I'm just genuinely excited. It should arrive tomorrow :)

---

### Post by aysiu on 2006-05-30
Is this for a dual-boot? Or Ubuntu only?

---

### Post by drfox on 2006-05-30
It's primarily for Linux. Since most pc's come with WinXP, I may dual boot just for Quicken and QB. Are there advantages to dual core vs 64-bit vs ???
Anything to steer away from?

Larry

---

### Post by aysiu on 2006-05-30
Have you taken a gander at this already?
[https://wiki.ubuntu.com/HardwareSupportMachinesLaptops](https://wiki.ubuntu.com/HardwareSupportMachinesLaptops)

---

### Post by hajk on 2006-05-30
[QUOTE=drfox]My 3-year old notebook hard drive just died. [/QUOTE]

Are you sure about the hard drive? I have a much older ThinkPad A22e with a 15GB hard drive that I thought had died as well: first some I/O errors that could be fixed with a reboot; then more errors; and finally I wouldn't even get the GRUB page to do an alternative boot of Win XP. Dead, I thought, after a hard and fruitful life...

Then I remembered Knoppix, inserted the liveCD and fired it up... no problem. Then I used cfdisk/mkfs etc to wipe the whole hard drive and install new partitions: /dev/hda1 64MB ext2 mounted on /boot; /dev/hda2 512MB swap; and /dev/hda3 14GB jfs mounted on /. I honestly believe it's this last choice of jfs that has blown new life into my old hard drive. I installed Dapper on it, and never looked back. Hard drive performing as new for the last couple of months. You think it's dead, but may be all it needs is newly made partitions formatted with a modern FS.:cool:

---

### Post by drfox on 2006-05-30
[QUOTE=hajk]Are you sure about the hard drive? [/QUOTE]

I tried Knoppix yesterday and reformatting failed, but I didn't wipe the drive before trying to reformat. I'll give it a try. Thanks!

Larry

---

### Post by Shay Stephens on 2006-05-30
I have had the hard drive fail on two laptops.  It's a lot cheaper to just buy and install a new hard drive ;-)

But not as fun as getting a new laptop hehehe

---

### Post by hajk on 2006-05-30
[QUOTE=Shay Stephens]I have had the hard drive fail on two laptops.  It's a lot cheaper to just buy and install a new hard drive ;-) [/QUOTE]

Oh really? New 15GB hard drive for ancient ThinkPad A22e lists at more than 400 euros (that's more than 500 bucks US). "Refurbished" drives list for something like 150 euros (almost 200 US) -- not really my choice of hardware. 

With those prices a person is better off buying a new laptop -- more than 5 year's use out of my ThinkPad is not too shabby, really.:cool:

---

### Post by Shay Stephens on 2006-05-30
[QUOTE=hajk]Oh really? New 15GB hard drive for ancient ThinkPad A22e lists at more than 400 euros (that's more than 500 bucks US). "Refurbished" drives list for something like 150 euros (almost 200 US) -- not really my choice of hardware. 

With those prices a person is better off buying a new laptop -- more than 5 year's use out of my ThinkPad is not too shabby, really.:cool:[/QUOTE]

Woops, I guess I should have said, it "might" be cheaper ;-)

---

