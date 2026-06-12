---
title: "After unning command &quot;init 1&quot; server is unconnectable :("
date: 2010-09-17
forum: General Help
---

### Post by clumpty on 2010-09-17
Running Ubuntu 10.04 32-bit

I ran the command "init 1" which kicked all users off immediately, which I expected.

The problem is now that no matter how many times I reboot the server, it can't connect to any other servers and refuses all incoming connections. I can connect through the console on the VPS's control panel, but that's it. Connecting normally through SSH just gets a refused connection. I'm very gimped now and I have no idea how to fix this.

I tried things like "init 3" but it doesn't help. I am also unable to back anything up, as I cannot make any outgoing or incoming connections other than through the java applet on the control panel. I tried to scp files through it but it fails.

Any ideas how to fix this? Or at least backup files so I can just wipe it? I'm dying here.

---

### Post by spjackson on 2010-09-17
Did you make another changes before your "init 1" command? Of itself, this should not cause the symptoms you are observing after a reboot.

When you log in on the console, what does "runlevel" report when run from the command line?

What's the output of dmesg (run from the command line)?

---

