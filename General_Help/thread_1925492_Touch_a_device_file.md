---
title: "Touch a device file"
date: 2012-02-14
forum: General Help
---

### Post by conradin on 2012-02-14
Hi all,
 Im looking to start writing some serial port programs, but my laptop doesn't have a /dev/ttys0 file, or an actual serial port for that matter. Ok, no prob right? I'll just make that file... Nope! touching a file evidently doesn't set a device file. So how can i create a device file for my serial port? (which doesn't actually exist)

I'm away from any other Linux box with a ttys0, so I cant just copy one. 
so how can I create this file?

---

### Post by dcstar on 2012-02-15
> **conradin said:**
> Hi all,
 Im looking to start writing some serial port programs, but my laptop doesn't have a /dev/ttys0 file, or an actual serial port for that matter. Ok, no prob right? I'll just make that file... Nope! touching a file evidently doesn't set a device file. So how can i create a device file for my serial port? (which doesn't actually exist)

I'm away from any other Linux box with a ttys0, so I cant just copy one. 
so how can I create this file?

**You don't**, the kernel creates them from actual hardware detected on startup.

---

