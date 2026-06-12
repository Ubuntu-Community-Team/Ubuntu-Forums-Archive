---
title: "Wierd Quircks of Ubuntu"
date: 2006-05-31
forum: General Help
---

### Post by InMSWeAntitrust on 2006-05-31
Hey, I've switched from winddoze to ubuntu, and I couldn't be happier, but there are a few discrepancies that I need to sort out, with you guys' help...

1. Whenever I leave the computer for extended periods of time, it logs out automatically (I usually leave it as a locked screen).  Where is the configuration for this, or is it a glitch, or what?

2. Whenever I leave my computer running, sometimes it freezes abruptly, often for 10 minutes or more, becoming very bogged down, it seems, when I haven't been running processor intensive programs (usually Azureus).  Is this normal, or abnormal???


Thanks in advance guys.

Long Live Open Source!

---

### Post by Horizon on 2006-05-31
[QUOTE=InMSWeAntitrust]Hey, I've switched from winddoze to ubuntu, and I couldn't be happier, but there are a few discrepancies that I need to sort out, with you guys' help...
1. Whenever I leave the computer for extended periods of time, it logs out automatically (I usually leave it as a locked screen).  Where is the configuration for this, or is it a glitch, or what?

2. Whenever I leave my computer running, sometimes it freezes abruptly, often for 10 minutes or more, becoming very bogged down, it seems, when I haven't been running processor intensive programs (usually Azureus).  Is this normal, or abnormal???


Thanks in advance guys.

Long Live Open Source![/QUOTE]

For the first one go to System>Preferences>Power Management and check the settings there. If everything there is fine it might be due to your screensaver crashing gdm. Try going to System>Preferences>Screensaver and see if it crashes you.

The second one may be your hard drive dieing. Try typing dmesg in the terminal after the next time it happens and see if it says anything.

---

### Post by InMSWeAntitrust on 2006-05-31
Thanks, I'll try the second one, but I don't seem to have a power management option...

I'm guessing it's vital, huh?

EDIT: Is there a way to clean the RAM and swap on-the-fly, because it seems my computer doesn't free those up when programs close (80% and 40% used of RAM and swap, respectively)

---

### Post by Horizon on 2006-05-31
[QUOTE=InMSWeAntitrust]Thanks, I'll try the second one, but I don't seem to have a power management option...

I'm guessing it's vital, huh?

EDIT: Is there a way to clean the RAM and swap on-the-fly, because it seems my computer doesn't free those up when programs close (80% and 40% used of RAM and swap, respectively)[/QUOTE]
You can launch the power manager throught the terminal with ```
gnome-power-preferences
``` if you're having toruble spotting it.

As for the Ram/swap usage question, memory should be freed when the offending programs are closed. As far as I know the only way to do it "on-the-fly" is to open the System Monitor tool, sort by Virtual Memory and kill the offending proccesses. I really can't be of much help in this area as I have never had any problems with swap/ram usage that wasn't solved by closing the offending program or process and starting it again.

Maybe someone else could offer advice on swap/ram usage? Anyone?

---

### Post by InMSWeAntitrust on 2006-05-31
```
gnome-power-preferences 
```
Doesn't open anything for me, and dmesg doesn't show anything unusual

It's just minor quirks, that are not as apparent after a reboot, don't worry too much about it, I will be getting rid of this computer soon and getting a better one for Ubuntu soon ;)

---

### Post by thesupremeg33k on 2006-05-31
As far as the ram/swap usage goes....don't worry about it as much.  From what I understand Linux deals with memory and swap space much more efficiently (therefore it uses more) than Windows so its normal to see high utilization of each.  How much RAM do you have?  80% of 512 MB isn't bad.  80% of 2 GB is pretty excessive IMO.

---

### Post by InMSWeAntitrust on 2006-06-01
I have 256mb of RAM and approx. 512 of swap.

EDIT: I went through dmesg this morning and found this:
[4325076.465000] oom-killer: gfp_mask=0x1d2
[4325076.465000] DMA per-cpu:
[4325076.465000] cpu 0 hot: low 2, high 6, batch 1
[4325076.465000] cpu 0 cold: low 0, high 2, batch 1
[4325076.465000] Normal per-cpu:
[4325076.465000] cpu 0 hot: low 62, high 186, batch 31
[4325076.465000] cpu 0 cold: low 0, high 62, batch 31
[4325076.465000] HighMem per-cpu: empty
[4325076.465000]
[4325076.465000] Free pages:        3060kB (0kB HighMem)
[4325076.465000] Active:29519 inactive:29110 dirty:0 writeback:0 unstable:0 free:765 slab:2624 mapped:56916 pagetables:475
[4325076.465000] DMA free:1080kB min:124kB low:152kB high:184kB active:5908kB inactive:5868kB present:16384kB pages_scanned:836 all_unreclaimable? no
[4325076.465000] lowmem_reserve[]: 0 239 239
[4325076.465000] Normal free:1980kB min:1916kB low:2392kB high:2872kB active:112168kB inactive:110572kB present:245632kB pages_scanned:0 all_unreclaimable? no
[4325076.465000] lowmem_reserve[]: 0 0 0
[4325076.465000] HighMem free:0kB min:128kB low:160kB high:192kB active:0kB inactive:0kB present:0kB pages_scanned:0 all_unreclaimable? no
[4325076.465000] lowmem_reserve[]: 0 0 0
[4325076.465000] DMA: 0*4kB 1*8kB 1*16kB 1*32kB 0*64kB 0*128kB 0*256kB 0*512kB 1*1024kB 0*2048kB 0*4096kB = 1080kB
[4325076.465000] Normal: 1*4kB 23*8kB 2*16kB 1*32kB 1*64kB 1*128kB 0*256kB 1*512kB 1*1024kB 0*2048kB 0*4096kB = 1980kB
[4325076.465000] HighMem: empty
[4325076.465000] Swap cache: add 148280, delete 148280, find 5392/7941, race 0+4[4325076.465000] Free swap  = 0kB
[4325076.465000] Total swap = 506036kB
[4325076.465000] Out of Memory: Killed process 7346 (Xorg).

Would that explain them both (out of memory)(random logoff)?

---

### Post by mbeierl on 2006-06-01
Yep.  The X server ran out of memory and was killed.  The solution is to figure out what is using all your memory.

What apps/etc are you running?

---

### Post by InMSWeAntitrust on 2006-06-01
Well, usually only GAIM, or a combination of GAIM, and Azureus (a java-utilizing app)

I seem to believe it's Azureus, but sometimes it does it when I just leave GAIM up.

---

### Post by InMSWeAntitrust on 2006-06-02
Well, I upgraded from Breezy Badger to Dapper Drake, and it seems I now have a power management choice, and I haven't had any problems (so far...)

So keep your fingers crossed ;)

---

