---
title: "soft lockup of CPU on boot [solved]"
date: 2009-06-29
forum: General Help
---

### Post by Zeke73SG on 2009-06-29
I am running Hardy on a desktop that I built on a Biostar motherboard which is also booting XP on a second HD. When I try to boot Ubuntu it freezes exactly the same way every time. Whether I use kernel 2.6.24-24 or 2.6.24-23 it will freeze at the Ubuntu splash screen. If I try recovery mode it will say that it is unable to read the root filesystem and then flash (for a fraction of a second, every ten seconds) "bug: soft lockup cpu 0 stuck for 11s! [modprobe:1487]".

As I was writing this post I tried to boot Linux again to see the actual wording of the "unable to read..." bit and the system started successfully.

Here's what I did. I ran memtest for 12 hours and there were no problems. Then I updated the BIOS and that didn't fix it. Then I made a new Knoppix disc and used it to run fsck on /dev/sda1 (my root filesystem) and it did not specify that there were any errors, but this was what seemed to fix the problem because now I am looking at my login screen.

The "soft lockup of CPU..." thing seems to be caused by a plethora of issues so it was hard to find out what was going on, and honestly I still don't know. I am only posting this now in hopes that someone else can use what I did to fix their system. Goodnight. -Zeke

---

