---
title: "System stops in random intervalls ..."
date: 2012-01-06
forum: General Help
---

### Post by vinterkind on 2012-01-06
Hi all,

I've got a serious problem with Ubuntu 11.10 running on a DELL Optiplex 990 Machine.
Whatever I do, the system randomly stops. Imagine you are working on a shell and randomly you
won't get a prompt. Or while typing the system stops and won't return to the prompt even if CTRL+C'ed.

I got the Hardware tested. Everythings fine. Memory, System (BIOS and so on, DELL has a pre-check-tool), Harddisk (smartctl health tests pass and so on) , Network (fine!) ...
And the problems remains even if I have no GUI and pure shell. 

The System Clock seems to stop randomly, but kernelparameters like noapic, nolapic doesn't help.

Although the Network is finely working, when I ping another machine you've got a package loss of 20%, caused by the system to stop randomly. (e.g. 20 pings out, 10 pings missing, 10 pings out, 40 pings missing)

The Magic SysRq Key seems to work, but I could not make out any help of the messages.

I don't know what to check now. Maybe you've got some suggestions ...
I'd appreciate your hints. :icon_frown:

---

### Post by 2F4U on 2012-01-06
Did you look into the system log files after it stops? Is the machine getting hot?

---

### Post by vinterkind on 2012-01-09
> **2F4U said:**
> Did you look into the system log files after it stops? Is the machine getting hot?

No nothing of that kind. I've skimmed through the logs, but I did not find any interesting message. 
And it isn't getting hot. But maybe, you've can suggest some keywords I haven't tried ?

---

