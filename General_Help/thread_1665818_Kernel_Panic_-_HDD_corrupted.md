---
title: "Kernel Panic - HDD corrupted??"
date: 2011-01-12
forum: General Help
---

### Post by loxaXcracker on 2011-01-12
Today I was running unetbootin for some tasks and it apparently didn't close properly. I noticed that ps aux | grep unetbootin was giving me a different pid each time (kept increasing) so I couldn't really kill it, and therefore didn't pay much attention. 

About 1 or 2 hours later, my pc started behaving strangely until I decided to reboot it and I got a kernel panic error. I couldn't really do anything (no shortcuts/combination worked). My only solution was to hold the power button until the PC would shut down, even though I think I heard a strange noise when it did.
After trying to start it up, it keeps showing that it's unable to boot from that HDD, though bios shows that it detects the drive.

I lost all of my linux distros disks and it's 2:31AM so I can't go out and buy another DVD right now to burn linux on it, which let me to try to look what Windows7 repair tools had to say. Well apparently it detects the HDD so it's not fried, but it shows that it's completely empty. You see, that's my biggest concern as the only thing that matters for me is the data from it.

I really hope that it's the EXT3 incompatibility of windows 7 with linux that causes it to show that the HDD is empty.

**Please please please tell me what to do!! Formating is not an option as I need to recover those files first! **

---

### Post by loxaXcracker on 2011-01-12
Currently trying to download ubuntu on my netbook and create a live-USB so that I could at least boot on my main PC and see if my files are still there. If they are I'll have to find a way to back them up and then format.

Please give more suggestions.. maybe there's a way to fix this? Maybe grub got broken? :( EVERYTHING was on that HDD I really need those files...

//Edit

I booted through backtrack4 live-usb and it seems that G-parted is finding the HDD as unallocated space.

---

### Post by loxaXcracker on 2011-01-13
/Bump..

---

