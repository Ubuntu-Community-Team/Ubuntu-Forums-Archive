---
title: "Some tips on using ddrescue with a flaky drive"
date: 2011-04-15
forum: General Help
---

### Post by fatherted on 2011-04-15
Tl;dr: Persistence is a virtue when recovering bad drives. Always look at syslog/dmesg to see what's actually happening to your hardware. Try different options. 

Full: 

A friend of mine recently whacked her laptop (I don't mean she took out a hit on it, I mean she apparently smacked it a little too hard closing the lid or something). 

This resulted in the hard drive becoming near-instantly borked, Windows wouldn't start, etc. 

Naturally, I fired up an Ubuntu livecd to take a look at it, and in the hour or so that she'd been messing with it (rebooting, rebooting again...) it had accumulated around 400 pending sectors and 10,000 or so SMART errors. Sadly, the G-sensor never got triggered. Presumably the threshhold was set too low on that, but...whatever. 

Anyway, I pulled the drive, snagged a same-model replacement from the Best Buy across the street (I didn't have any SATA 2.5" drives around, all my hardware is old :P, and she needed the data ASAP for work - of course). 

I spent something like 12 hours experimenting with various combinations of dd_rescue, dd_rhelp that I'd been familiar with from back in the day, and eventually discovered the shiny new gnu-ddrescue utility which is much nicer. 

However, whatever I tried, I couldn't get more than about 100MB of data recovered - the first Dell hidden partition (~40mb) and the first chunk of the recovery partition.  

I tried manually creating the needed partitions on the new drive and recovering only the system partition (where the important stuff was) I tried a direct device-to-device copy - nothing seemed to get past that. Many different option combinations for ddrescue, etc.

It turned out upon looking at dmesg, the drive seemed to be becoming *completely* unresponsive sometimes. ddrescue would for some reason interpret this as read errors, skip all remaining blocks, and start trying to split the failed blocks to find the next good spot - but since the drive was unresponsive, it would just run forever and not find anything. 

I found that by hot-unplugging SATA power and replugging it, (unplugging the SATA cable didn't do it - hard power cycling the bad drive was the only thing that would bring it back on line) - I could get another few MB before it died. 

After slowly chugging my way through about 1GB of data 4 or 5 MB at a time this way, it seemed to find a groove and is now merrily working away. I still have to do the unplug/replug bit now and then but I've got over 3GB now, 2GB of which was in the last thirty minutes, and I'm hopeful that I'll eventually get it all. It's a 250GB drive, but had very little on it other than the Windows install and documents which don't take up much space.

Also of note is that putting an ice pack on the controller board of the drive made things *noticeably* better - but I live in an extremely dry climate where condensation isn't an issue, so be careful.  

The option set that is working for me is: 

root@Hal:~# ddrescue --direct --retrim --try-again --max-retries=-1 /dev/sdf /dev/sde /root/wholedisk.log

Hopefully this helps somebody.

---

