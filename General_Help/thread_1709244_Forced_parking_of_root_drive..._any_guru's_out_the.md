---
title: "Forced parking of root drive... any guru's out there???"
date: 2011-03-17
forum: General Help
---

### Post by 1branchonthevine on 2011-03-17
We have a server with a standard desktop hard drive in a mobile (APC-UPS) server rack that has to be moved over a bumpy door trim every week. To avoid risking damage to the drive, we shut down the system every time we move it. There has to be a better way... maybe to force the root drive (and/or others) to momentarily go in parked-head mode until further user input says otherwise.

I have found many forums mentioning how to DISABLE drive parking, but none have mentioned how to force-park a drive; nevertheless the root drive. I did stumble over a Winblows command called "park," but I ventured no further as my actions might give some form of wacked out credit to the Winblows freaks out there!

More concerns:
The drive has no g-force sensors in it... sorry!

Lesser preferred option 1: "forced spin-down mode." I know a drive can spin  down after x minutes  of inactivity, but then I'm toast if the  mouse moves and clicks firefox  when moving the rack over the bump. So, is there a command to force   spindown for x whatever? I prefer not to use this command because of the  extra mechanical drive stress, and still favor parking over spinning  down (the lesser of the two evils since spindown also parks the drive  regardless). 

A lesser preferred option 2: nor do we want to put the  system in hibernate, since we would simply  favor rebooting to save the  time. I don't think "suspend/standby mode"  forces drive parking does it,  because the drive is typically still  running? Is there a way to confirm it's parked? Plus the double evils comes into play with this option as well!

Thanks... awesomeness!

---

### Post by tgalati4 on 2011-03-17
If your rack server has a hot swap drive then just pull the drive out.  Linux should just patiently wait for drive IO until you plug it back in.

You can try to use hdparm -y or -Y parameter, but Linux will probably just wake the drive up again for any IO request.

I agree that hibernate takes the same amount of time as a cold boot.  Sleep should only take 5 to 10 seconds but I don't know if the server version of Ubuntu has the sleep scripts installed.  You would have to use the desktop version to get sleep to work correctly--and then it depends on the acpi and BIOS of the server to behave.

---

### Post by 1branchonthevine on 2011-03-18
*Actually it is a simple desktop pc (no hotswap tray, but is a SATA drive) running ubuntu desktop (we use it back and forth for slide shows and a 2-4 feed, looping video stream server, the rack simply holds the pc, a projector, and makes it easy to lock up the other goodies).*

So you are saying the hotswap feature will work on a mounted (root) drive? Is there a command to initiate a hotswap transition, because simply pulling the drive out while it is running is still potentially damaging to the heads/platters, especially with larger GB economy drives. If there is a command, can I simply NOT pull it out, yet have it still be powered down or in the parked position?

Regardless, it would be useful to know how to tell if a drive is parked or not.... any suggestion that doesn't require a spindown operation will be hard to assure whether the drive is parked or not.

---

