---
title: "CD + DVD Burning Issues!"
date: 2006-06-18
forum: General Help
---

### Post by ol1v3r on 2006-06-18
Hello there!

I've had this issue for a long time now, but i've got to a point where I actually need it :[

It appaears no matter what I use (NeroLinux, Nautilus, Gnomebaker or K3b), the pre-burning processes always crashes or stalls with no real error or no sign of what could be causing it, which is a pain for diagnostics!

I was just wondering if anyone else had the same problem with this distro.. As its really quite annoying, as I need to burn alot :[

I'm using two NEC drives, a 1300A and a 4550A

I'll try to answer any questions as best as I can :]

Thanks,
Oliver

---

### Post by Jasper Houtman on 2006-06-18
Works like a charm with my LG drives. 

Sounds like the problem is with your writer.

Did you try updating the driver?

---

### Post by ol1v3r on 2006-06-18
[QUOTE=Jasper Houtman]Works like a charm with my LG drives. 

Sounds like the problem is with your writer.

Did you try updating the driver?[/QUOTE]

The driver? Or do you mean the firmware? I didint realise you could install NEC Drivers :]

Update: .. Had a look at dmesg, found this:

> [17179642.640000] cdrom: This disc doesn't have any tracks I recognize!
[17179705.688000] ide-cd: cmd 0x3 timed out
[17179705.688000] hdc: lost interrupt
[17179765.688000] hdd: lost interrupt
[17179825.688000] hdc: lost interrupt
[17179885.688000] ide-cd: cmd 0x3 timed out
[17179885.688000] hdd: lost interrupt
[17179945.688000] hdc: lost interrupt


Thanks,
Oliver

---

### Post by Kinslayer on 2007-04-16
I had a problem with long startup & shutdown times.  The problem was my cd rom & dvd rom weren't mounting properly.  They were attached to the same ide cable.  How I fixed it was I shutdown the system, unplugged the cables from each, & rebooted.  It started right up.  Aha.  I shutdown again, which took less than a minute instead of the usual 5-10 minutes.  I connected one drive, started up, & it loaded quickly.  I repeated this with the second drive, with no problems.  A third time with both booted up quickly, and it hasn't been an issue since, at least for the couple of days since I've done this.

---

