---
title: "Ubuntu + PXE + Persistent Mode"
date: 2009-10-20
forum: General Help
---

### Post by RipTorn on 2009-10-20
Hi All,

I'm wondering if anyone has had a look at the ability to PXE boot Ubuntu (Which I have working flawlessly with Ubuntu Jaunty) but with the added bonus as persistent mode. 

The main problem I think I am having is that /cdrom/ gets mounted from the nfs share but ubuntu automatically mounts this as read-only thinking its just a normal cdrom from a live cd so having casper-rw there is usless. 
On the USB stick you need to have casper-rw in the root partition of the USB which comes up as a fat32 hardrive which doesn't get mounted as read-only.

Anyone think of a way around this?

---

### Post by RipTorn on 2009-10-25
So no one is sure?

---

### Post by marcb_ro on 2011-03-24
I'm bumping this because i'm interested in building a cluster at my university.

All the machines are running windows, but they have this cool feature in the BIOS, *Wake On Lan with PXE boot*, so i can wake them up when they're not in use, boot ubuntu and run mpi on them.

I tried editing /usr/share/initramfs-tools/scripts, and change ```
nfsmount -o ro
``` to ```
nfsmount -o rw
```
That didn't seem to do the trick.
I would appreciate any help.

---

