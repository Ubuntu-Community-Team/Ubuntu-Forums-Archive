---
title: "Computer has been crashing a lot"
date: 2010-09-01
forum: General Help
---

### Post by blur xc on 2010-09-01
My desktop pc running Ubuntu 10.04 64bit, has been locking up a lot recently and has been needing frequent hard resets.  It's really irritating.  Is there some way to diagnose what is causing the system to crash like that?

The alt-prtscrn-REISUB trick doesn't even work, let alone ctrl-alt-f1 or anything.  It's just locked up solid, 100% unresponsive to everything except the power/reset button.

thanks,
BM

---

### Post by MooPi on 2010-09-01
This could be many things and I suspect it is a hardware issue. The first thing you should do is boot from the live Ubuntu CD and run memtest to check your ram. Let memtest run through the test at least twice completely to ensure a thorough check.  If the ram is clean without error you should check your hard drive for problems.
 Boot again from the live CD and open a terminal. ```
sudo e2fsck -n -f
``` This will force check but not make any corrections. It is also important that you not mount any drive before or during this check. Just let the test run. If errors show up ,start and run from terminal again ```
sudo e2fsck -p
``` This will attempt to correct any drive error. If you run both tests and nothing shows up, you may need to have your power supply checked by a technician.

---

### Post by blur xc on 2010-09-02
Thanks for the response- I'll run memtest tonight before bed.  It takes a long time to run, doesn't it?  I've suspected there was something wrong with my ram for a while now, so I'm hoping that's it.  It won't boot if I put the ram in the mobo in dual channel mode, and my conky reports 3.89gb of ram instead of 4gb.  I don't know if that's because of the whole kilo-byte vs. kibi-byte bs though, gskill fudging the numbers.  I know hdd manufacturers do that, but I didn't think they did that with ram so I don't know.  Can I just rum the memtest from the grub screen, or do I need to boot the live cd?

It doesn't happen that frequently so it's kind of hard to diagnose.  Once every couple of days it'll have an issue, but the day I posted this- It froze up maybe three times in that 24hr period.  I can normally have 5 day up-times when everything is running smooth.

Thanks again-
BM

---

### Post by llawwehttam on 2010-09-02
I used to get this occasionally albeit very rarely. I fixed it but can't remember how.

From what I can remember it was a known 64-bit kernel bug that affected different pc's differently.

---

### Post by blur xc on 2010-09-22
> **llawwehttam said:**
> I used to get this occasionally albeit very rarely. I fixed it but can't remember how.

From what I can remember it was a known 64-bit kernel bug that affected different pc's differently.

Well, I ran those tests and the problem persists.  Every few days or so, it just freezes up.  Now, I have no idea if the whole pc is freezing, our just the mouse and keyboard input.  My wife just called me a few minutes ago from home, because she was using the computer and out of nowhere the mouse pointer quit moving.  No keyboard combination would do anythign (ctrl-alt-f1, etc...)...  But I didn't have her try the alt-prtsc-REISUB trick (she'd be annoyed if I told her to do that over the phone).

Anyway, if anyone has any better solutions I'm all ears.  If I did a dist-upgrade would that load a new kernel?  Is it worth trying?

Thanks,
BM

---

### Post by 7h3d4rk0n3 on 2010-09-23
First thing you should try, is disabling Compiz if using it, and the Desktop effects if you have them on. If that doesn't work, then it is probably hardware related. Perhaps over heating?

---

