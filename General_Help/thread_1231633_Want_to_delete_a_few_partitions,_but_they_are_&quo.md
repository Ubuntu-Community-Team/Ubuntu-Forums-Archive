---
title: "Want to delete a few partitions, but they are &quot;locked&quot;"
date: 2009-08-04
forum: General Help
---

### Post by The Toxic Mite on 2009-08-04
Hello!

I have Windows XP and Ubuntu 9.04 installed side-by-side, but I want to get rid of the Ubuntu 9.04 partition (ahem, pardon my French ;)).

So I booted into the LiveCD, and on GParted it tells me that /dev/sda2 is locked, and I want to UNMOUNT it but it won't let me. I need to unmount it so I can delete it, but how do I do that?

---

### Post by lisati on 2009-08-04
Suggestion: turn off swapping. Right-click on the swap partition. If "swapoff" (NOT "swapon") is listed as an option, click on that.

---

### Post by Glyndwr on 2009-08-04
> **The Toxic Mite said:**
> Hello!

I have Windows XP and Ubuntu 9.04 installed side-by-side, but I want to get rid of the Ubuntu 9.04 partition (ahem, pardon my French ;)).

So I booted into the LiveCD, and on GParted it tells me that /dev/sda2 is locked, and I want to UNMOUNT it but it won't let me. I need to unmount it so I can delete it, but how do I do that?

what error does it give you when you try to unmount it?

There is probably a process holding a file on the filesystem open.

You could try

fuser <filesystem>

e.g fuser /opt

That should give you the PID of the process that is holding files open.

---

### Post by michy99 on 2009-08-04
Is sda2 an extended partition with other partitions inside? If so, they must be unmounted first. If one is a swap partiton, you have to make sure that swap is off.

---

### Post by dcstar on 2009-08-05
> **michy99 said:**
> Is sda2 an extended partition with other partitions inside? If so, they must be unmounted first. If one is a swap partiton, you have to make sure that swap is off.

Yep, even booting off a Live CD uses the swap partition on the hard drive, use the Gparted function to "Swapoff" and then things can be changed.

---

