---
title: "No Sound ... Period"
date: 2011-06-28
forum: General Help
---

### Post by Velvet Karuda Leopard on 2011-06-28
I put this in General Help because I am not sure of the nature of this problem.

Just this morning our power went out while this PC was in use.  When the power came back on all seemed well, until my brother tried to play a game, Doom 3.  We found that the sound was out.

Upon investigation we found that all sound of any and all kinds were out, even DVD playback, flash, alerts, everything.

I have repaired, purged, reinstalled, and updated all the sound related modules and drivers there are and repeated with no results.

My speakers work fine and the OS, 10.10, is detecting the sound card, integrated into the motherboard, but not detecting the speakers themselves, except intermittently.

I have tried editing the various files and nothing.  I hope my motherboard isn't fried in some way.

I have checked the BIOS on the board and they seem fine as well.

This is not a fresh install or upgrade.  It has been running perfect ever since Maverick first came out.

Is there anyone who can help me out at least in finding the reason why my sound is out.

---

### Post by WorMzy on 2011-06-28
Try booting a liveCD. Does sound work on that? If no, then you have a hardware problem. If yes, then you have a software problem.

---

### Post by Velvet Karuda Leopard on 2011-06-28
Ok.  I am in the process of DLing an Ubuntu disc now.  I can use this as a liveCD, correct?

When I get the results I will post again.

---

### Post by WorMzy on 2011-06-28
Yes. I'm curious as to how you installed Ubuntu in the first place, if you don't have an installation disk (or USB)?

---

### Post by Velvet Karuda Leopard on 2011-06-29
Yeah, about that.  This is my little brother's PC I built for him and he cannot find the disc we used to install 10.04 in the first place.  We updated to 10.10 through software.

But as I said before the 10.10 update was working flawlessly with zero hickups, period.  I am VERY happy with Ubuntu's performance.

I am sure the power outage was at fualt and looking around I do believe it was a file system fudge up caused by the outage.

It gives me a neat idea for a filesystem/general-memory storage facility either in software or hardware though.  I am currently in a class right now, but as soon as I get home, and perform a complete front end brake job on my grandma's four by four Dodge, I I will do a frsh 10.04 LTS install.  Luckily my brother had all his data backed up on my external hard drive and all he has to do is get his apps again and reinstall his games.

I have heard that UPS units were overkill except for what the poster called "rural conditions".  I do live in a rural area with a highly questionable power grid.  Do you guys think it would be worth the investment for me to buy a UPS and if so are there any suggestions on brand, stats, and the like.

I thank you for your responses and will post my results later.

---

### Post by WorMzy on 2011-06-29
It certainly seems like a UPS would be a good idea in your situation. Still, if you suspect filesystem corruption, there's no need to reinstall to fix that. Ubuntu comes with a filesystem checker (fsck) which can be used to scan and repair certain linux filesystems (ext#, xfs, jfs, etc). You can't (or at least, *shouldn't*) run fsck on a mounted filesystem though, so you'd need the liveCD for that too.

I can't give any advice regarding UPSs, they're not something I have any experience with.

---

### Post by Velvet Karuda Leopard on 2011-06-29
Well, I have a LiveCD and am on it right this minute.  Still no sound ... period.

Does this mean my motherboard is scrap?

Would a sound card fix this issue?  Being that this board is currently running on board sound.

---

### Post by Velvet Karuda Leopard on 2011-06-29
Okee.  I tried three sets of speakers and one set of headphones on all audio outputs and ziltch save for some nice popping and hissing.

Starting to believe it is the board.

But I have a question, and please don't laugh at me:  Could the problem be a bad or corrupted BIOS and how do I redo the BIOS if so?

I still have the entire contents of the box the motherboard came in, Support DVD and all.  Could I, somehow "reinstall" the motherboard?

If I can and it would require a fresh OS install, I would be okee with that.

Thanks for any reply.

---

### Post by WorMzy on 2011-06-29
If it is the motherboard, I'd recommend that you replace it, rather than trying to circumvent the problem by buying a soundcard. Using damaged electronics is asking for trouble.

The good news is, replacing the motherboard won't kill the Linux installations. You may not even need to regenerate your initrd(s). I had to downgrade my main PC's motherboard (+gfx card, +RAM) just last year (coolant exploded all over), and although Windows *does* require a reinstallation, Ubuntu continued to just work as though nothing had changed.

Regarding the bios, I sincerely doubt that it's become corrupted. If it had, I'd expect the PC to not even POST, let alone boot. You can flash the bios if you really want to, you'll probably need a floppy disk (and drive) for that though. You might be able to do it with a USB stick, if your motherboard supports booting from them. You'll need to check your motherboard manufacturer's website for the bios files, as well as specific instructions on how to flash it. It's a risky process (flashing the bios, not getting the files/reading the instructions); if it fails, for whatever reason, you might be left with a completely unusable motherboard.

---

### Post by Velvet Karuda Leopard on 2011-06-29
Well, crap crap and crap again.

I did a full fresh install and nothing, but a pop here and there.  Did the ful updates and all the drivers, plugins and nodda.

My board NEVER did a POST, ever since it was installed.

Well, I guess I will have to replace the board.  Not sure when he will get the scratch for it though.

It is an Asus M4A88T-V EVO/USB3.0 what would be a safe replacement if I cannot find the exact board?

Many thanks to all who replied to try and help.

I will get me a small UPS to guard against anything further and I am definitely going to raise Caine to the electric company.  Their faulty grid and shoddy work caused the outage in the first place.

---

### Post by WorMzy on 2011-06-30
A "safe" replacement, would be any that has the same processor socket (e.g. LGA775, AM2, etc.), and the same RAM sockets (e.g. DDR2, or DDR3), and enough sata connectors for all your hard/cd/dvd drives (if applicable). If your board has integrated graphics, you're going to want to find another one with integrated graphics, or buy a separate graphics card.

---

### Post by Velvet Karuda Leopard on 2011-07-01
Thanks for the info.

I found the exact board and will get it.

I am also getting a 1000VA 600 Watt 30 Minute UPS.

O am also getting a graphics card, sound card, and another LCD monitor to dual display.

---

