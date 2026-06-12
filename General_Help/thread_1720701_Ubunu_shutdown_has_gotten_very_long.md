---
title: "Ubunu shutdown has gotten very long"
date: 2011-04-03
forum: General Help
---

### Post by campbuds on 2011-04-03
In the last month or so (don't recall exactly) Ubuntu 10.04 has gone from shutting down very quickly to taking up to 5-10min.

Any ideas or help would be appreciated. The only changes I have made are updates.

It hangs when it says it should be powering off

---

### Post by ajgreeny on 2011-04-03
At the grub menu (hold **shift** at boot up if you don't normally see the grub menu) hit "E" on the line you want to boot, then use the cursor keys to get to the kernel line and delete the words **quiet** **splash** at the end, then hit Ctrl+X to boot.  This change will only happen for this boot, not after that.

Your boot sequence, and the shutdown for that boot session will show text rather than a blank screen or plymouth.  At shutdown you may be able to see at what point the slow-down occurs, and what is supposed to be happening, but is obviously not working as it should.

---

### Post by campbuds on 2011-04-03
still need help

---

### Post by campbuds on 2011-04-05
ok, it is hanging again.

it only hangs when it is turned on and used a while.

It hangs at turn off. It gets to the point when it says it is unmounting and then powering off and it just hangs there for 5min before the computer actually shuts off.

---

### Post by campbuds on 2011-04-07
still looking for help with this!

---

