---
title: "Suspend then eventually Hibernate ?"
date: 2009-11-23
forum: General Help
---

### Post by inspiral on 2009-11-23
Hi All

This is reposted from the Hardware forum as I didn't get any help there.
 
 I've got 9.10 installed on an system based on an ION Atom 330 motherboard, an Asus AT3N7A-I to be exact.
 
The main requirement for this system is to be a reasonably efficient file and Squeezebox server, to facilitate this I'd like it to Suspend after a period of time when not being accessed then eventually Hibernate but be ready to WOL when required by another system or device on the network.
 
Currently the system quite happily Suspends and then will WOL when required but I don't know how to get it go from Suspend to Hibernate automatically when left for long periods unused.

If I manually power the system into Hibernate then it' will WOL ok it's just the automated move from Suspend to Hibernate that I don't know how to do.

FYI My MSI Wind(Atom) running XP quite quite happily performs this function.

Any ideas ?

Thanks in advance.

---

### Post by blazemore on 2009-11-23
I don't think this can be done with current software.
It may be possible with a bit of hacking.

One thing that could maybe work is instead of suspending the computer, run a script that does the following:


[LIST=1]
[*]Suspend the computer
[*]Wake the computer after a certain amount of time (If this is possible)
[*]Immediately hibernate the computer
[/LIST]
If the computer is woken manually, the script should terminate.
That's how I would do it, anyway.

---

### Post by inspiral on 2009-11-23
Thanks for the suggestion Blazemore, I guess you'd have to get the Ununtu power manager to run the script instead of just suspending, I don't know how to do this bit guess it wouldn't be too hard, I suspect the difficult bit would be getting the system to come out of being Suspended to then go into Hibernate mode.

>> FYI My MSI Wind(Atom) running XP quite quite happily performs this function.

I've had a look how this works and it's not the bios but the power manager in XP that handles this, you just set how long want to wait before it goes into Suspend and then subsequently (comes alive again) to then go into Hibernate.

Anyone else got any ideas ?

Cheers

---

