---
title: "computer freezes randomly"
date: 2006-04-10
forum: General Help
---

### Post by angryfix on 2006-04-10
My laptop will freeze for absolutely no reason and be completely unusable until rebooted. Here are my basic computer specs:

Dell Laptop Inspiron 600m (about 2-3 years old)
OS: Breezy Badger 5.10 (The only OS installed)
RAM: 512MB
CPU Speed: ~1.4Ghz

This problem just started within the last 24 hours and I can't pinpoint a catalyst. I'm actually more dumbfounded because it's not related strictly to Breezy, but I'm not exactly sure where to even start troubleshooting this (please move this thread if it's placed incorrectly). My computer also froze when loading GRUB, and it also froze when booting from a Knoppix live cd. Basically, it's unpredictable. Any ideas or jumping off points? Thanks.

---

### Post by Ramses de Norre on 2006-04-10
Could it be a heat problem?

---

### Post by greenpenguin on 2006-04-10
Try checking that your hardware is not defective, or doesn't support Linux.  Heating sounds appropriate - do you have heat sensing options in the BIOS you can play with?

---

### Post by angryfix on 2006-04-10
Thank you for the quick replies.

I first concluded that it may be a heating issue, but I let my computer sit all night while turned off to cool down, and it still froze within a few minutes of booting. I checked the BIOS settings for a section on heat control, and it doesn't have one. But guess what? It even froze while browsing the BIOS settings! This is definitely not going very well.

---

### Post by Ramses de Norre on 2006-04-10
Sounds like a hardware problem then. I'm not sure which hardware is used when you're in bios setup.

---

### Post by angryfix on 2006-04-10
So does it sound like this could be executed as *Operation Pray the Warranty Covers This*? I hate for this to be outside the scope of what I can manage, but it seems pretty serious.

---

### Post by sylvester_0 on 2006-04-14
Hmm I'm having the same problem as you. I suspected it was my 2x256 sticks, so I bought a new gig stick and left just that in there. Any live CD freezes eventually. It may take 10 mins, it may take 2 hours, but I eventually get an error that says something like CPU0: Soft lockup detected. It will freeze for about 20 seconds then work for 1 second then freeze for another 20. It is VERY annoying and makes it impossible to work. I had a cat /proc/acpi/thermal... up right when it started freezing and it was at like 56* C. Right now I installed Windows XP and I'm trying to get the stuff off my /home partition. Was there a change in the kernel somewhere along the line? I also saw a few errors relating to the IPW2200 firmware. I'm going to try and wipe the whole disk and install Flight 6 after I finish grabbing my /home.

Off topic, more linux/mobo problems for me. I just got a A8N32-SLI and it seems to be VERY finicky with the BIOS settings. If I change anything Windows won't boot and any time I try to boot/install linux it stops at Loading Linux Kernel :( *sigh* Anyone else have experience with this board?

---

### Post by sylvester_0 on 2006-04-14
Ok, it just started doing it in windows. Time to call dell.

---

### Post by albertobob on 2006-04-26
I am having the same problem, it just started a couple days ago, sometimes i can go hours without this happening, including suspending to ram several times.  I have been running ubuntu (breezy 5.10) sense mid November.  I run a dell D600 with 1280mb ram, and the original hard drive which came with the system.  I can't think of any changes i made it just started to happen.  My xp pro is on a separate dive, not a partition so i might try running it for a while and see if it locks up to.  although right before it freezed the last few time the Ethernet seems to die.

---

### Post by echo $USER on 2006-04-26
I've got the same problem on my IBM T21 800mhz Athlon, 128mb ram, but I'm sure it is a heating issue.  It only happens when I'm kicked back in the recliner with it in my lap.  I got it of ebay and only need it for a couple of months for this class I'm taking.  Once I'm finished with it in August I'll punt it off onto someone else.

---

### Post by echo $USER on 2006-04-26
[QUOTE=sylvester_0]Off topic, more linux/mobo problems for me. I just got a A8N32-SLI and it seems to be VERY finicky with the BIOS settings. If I change anything Windows won't boot and any time I try to boot/install linux it stops at Loading Linux Kernel :( *sigh* Anyone else have experience with this board?[/QUOTE]

I wish I had; that board is ill.  I'm still rocking a Abit AA8-Duramax.  Once the new AMD architecture is out and stable,  I'm ditching intel.

---

