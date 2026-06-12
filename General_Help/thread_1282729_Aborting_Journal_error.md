---
title: "Aborting Journal error"
date: 2009-10-04
forum: General Help
---

### Post by haemphyst on 2009-10-04
OK...  Finally the beta of 9.10 is out, and I upgraded my working wubi install of 9.04.  All of the updates and app seem to be working perfectly, except for the shutdown function.

The GUI goes away correctly, but I get an error:

[RUNNINGTIME] aborting journal on deviceloop0
[RUNNINGTIME] buffer I/O error on deviceloop0 logical block 3765833

No matter what I do, CTRL+ALT+DEL gets me an additional few lines after the above posted ones, (if needed, I'll get them, but I don't have them currently) and I can never get the system to shut down or restart.  I have to hard power-cycle.

Suggestions?  I know little to nothing regarding the CLI, so if somebody has suggestions, or needs something from a log, I'll need exact command texts.  I am not afraid to explore, and I want to know more, but I'm still very fledgeling in it.

I know this is an actual error, and it IS a new one...  the system ran perfectly, and shut down/rebooted perfectly before the 9.10, and so if I can get this fixed, that'd be awesome!  Thanks in advance for any help!

---

### Post by JC Cheloven on 2009-10-04
Hi, 

Not to blame you, but you shouldn't use alfa or beta software unless you're an experienced user, and not affraid of having occasional, even frequent, hang-ups and other problems.

And of course, you shouldn't compromise your main, working system (which probably you nedd for productive tasks) by "upgrading" it to an alfa or beta version that may be broken at a given time.

If you want to help the developpers testing new versions (that is what alfa and beta releases are public for), please install it on a dull computer, or at least in your main computer but in a separate partition for dual booting.

Plus you're on wubi, not a regular install. I'd try to help with your problem, but it makes little sense as it will surely be solved by the work in progress. I would go back to the current stable release 9.04, and wait for the final release of 9.10. Plz, don't be so eager ;-)

---

