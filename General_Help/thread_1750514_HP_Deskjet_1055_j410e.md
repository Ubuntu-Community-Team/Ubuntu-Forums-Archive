---
title: "HP Deskjet 1055 j410e"
date: 2011-05-05
forum: General Help
---

### Post by clinto on 2011-05-05
MACHINE: Compaq Presario5000
OS: Lubuntu 11.04
PRINTER: HP DESKJET 1055 j410e

So, I'm having weird issues.  This is the course of events:
- Installed Lubuntu 10.10 on a client's old Presario5000, no native drivers, installed HPlip, got it to print and scan fine.
- Got a call a week later saying it wouldn't work at all.  Go back, try different things, doesn't do a thing.
- Took both the pc and printer back to my house, hooked printer up to Win7, installed driver, works fine.
- Installed Lubuntu 11.04 on client's Presario5000.  Checked to see if it had native drivers, it was recommending 1100C drivers, tried it, didn't do a thing.
- Downloaded and installed HPlip 3.11.3a.  Ran chmod 700 on the run file.  Commanded ch on run file.  Chose automatic option.  Then it tells me I'm 8 required dependencies, but only lists gcc as one of them.  It then says that it can't install the dependencies due to version of the distro.
- Open Synaptic Package Manager, search for gcc, install it, go back to hplip, try it again, still says 8 dependencies missing and only lists gcc as one of them.

So, should I install EVERYTHING in my package manager that has to do with gcc?  I'm kind of at a loss, and I've been battling this thing for a week now, hate printers HATE PRINTERS.

---

### Post by clinto on 2011-05-05
Well if this doesn't work tonight, I'm going to have to install XP, as per request, which will run like crap on this old thing, and is going to be used by someone who will install every type of malware known to man.

I tried installing just about everything to do with gcc, it's still giving me the same thing.

If it's because hplip isn't compatible with new release of Ubuntu, HP needs to get on that, lots of linux users using hp printers... I bought this printer for this guy because I half expected it to just work in Ubuntu.  They always used to...

---

