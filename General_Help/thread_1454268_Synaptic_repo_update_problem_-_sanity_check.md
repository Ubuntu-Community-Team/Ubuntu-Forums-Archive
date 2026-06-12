---
title: "Synaptic repo update problem - sanity check"
date: 2010-04-14
forum: General Help
---

### Post by MichaelBurns on 2010-04-14
The purpose of this thread is a sanity check.  I attempt to activate the universe repo through Synaptic:

- System > Administration > Synaptic Package Manager
- Settings > Repositories
- Check universe; click "Close".
- "Repositories changed" dialog pops up; click "Close".
- Click "Reload".
- "Downloading Package Information" dialog pops up; let it finish.

However, packages that I "know" should now be available (e.g. sound-juicer) remain unavailable.  Even when I open a terminal to apt-get install, the package cannot be found.  Then, somehow, the next day I am able to apt-get install the package.

What's going on?  Is this procedure correct and complete?  Or am I missing a step.  Alternatively (and preferred, if possible):  is there a way to change the repositories on the command line without manually text-editting the sources.list file?

---

### Post by booksnmore4you on 2010-05-05
*Bump*

In my lucid 64, I cannot add repos by opening Synaptic > Settings > Repositories.  When I do that, it just updates them - no dialog appears.

---

