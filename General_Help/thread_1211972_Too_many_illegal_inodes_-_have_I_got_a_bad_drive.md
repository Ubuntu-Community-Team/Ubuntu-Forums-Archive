---
title: "Too many illegal inodes - have I got a bad drive?"
date: 2009-07-13
forum: General Help
---

### Post by dave_i on 2009-07-13
Hi everyone,

I built a new system a few days ago, and I've got Ubuntu 9.04 64-bit installed on a 500GB Samsung SATA drive. I was using firefox earlier, and the system started behaving a bit weirdly (terminal windows were completely blank etc.), so I rebooted. While it was rebooting, it started doing a drive check (I did a soft reboot), then threw an error and booted into a root shell. I ran fsck and got several messages, including "Too many illegal inodes", which I fixed and it seems to be running ok now. What I'm wondering is: is this purely a software issue, or have I bought a bad drive (bought 4 days ago).

Thanks,

Dave.

---

### Post by HavocXphere on 2009-07-13
> What I'm wondering is: is this purely a software issue, or have I bought a bad drive (bought 4 days ago).
Could be either. Difficult to say.

Have you done any hard-resets or had power-outages?

Also, listing the type of filesystem you're using is kinda required information for these kinds of questions.;)

The manufacturers usually provide a tool for testing HDD intergrity on their sites (although it is usually a windows apps).

Also look at the drives SMART data and the system logs.

---

### Post by az on 2009-07-13
Does S.M.A.R.T report a problem?  You can also scan every block with "badblocks".

[https://help.ubuntu.com/community/FaultyHardware](https://help.ubuntu.com/community/FaultyHardware)

---

### Post by dave_i on 2009-07-13
Thanks for the replies!

I did have to do a couple of hard resets, so it's possible that's the reason. I'm going to run Samsung's HUTIL checker from a usb stick just to make sure.

I'm using an ext3 filesystem. Everything seems to be running OK so far. For some reason, the S.M.A.R.T. functionality for my hard discs is disabled by default in the BIOS - I meant to get round to enabling it, but I forgot... Apart from a tiny reduction in performance, there isn't any reason not to enable it, is there?

---

### Post by az on 2009-07-13
> **dave_i said:**
> Thanks for the replies!

I did have to do a couple of hard resets, so it's possible that's the reason. I'm going to run Samsung's HUTIL checker from a usb stick just to make sure.

I'm using an ext3 filesystem. Everything seems to be running OK so far. For some reason, the S.M.A.R.T. functionality for my hard discs is disabled by default in the BIOS - I meant to get round to enabling it, but I forgot... Apart from a tiny reduction in performance, there isn't any reason not to enable it, is there?

S.M.A.R.T works inside the hard drive's system - there is no impact on performance whatsoever.

---

### Post by dave_i on 2009-07-13
Cool, thanks! I'll enable it now.

---

### Post by HermanAB on 2009-07-13
Do you have a UPS?  All computers work better and last longer on clean power.

---

