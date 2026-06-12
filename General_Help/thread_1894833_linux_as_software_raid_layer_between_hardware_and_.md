---
title: "linux as software raid layer between hardware and win 7 - how much overhead?"
date: 2011-12-13
forum: General Help
---

### Post by 4evrplan on 2011-12-13
I had this idea that 1) SSDs rock 2) they're very expensive 3) people give away their old USB flash drives like candy at halloween and 4) these could be combined in a RAID 5 to get performance much better than a HDD and have superior reliability.  Low cost, high performance, reliable.  Win, win, win.  Problem is, I use Win 7, and it doesn't support software RAID 5.  "What are you doing here" you ask.  I'm getting to that.

My idea is to use Linux running Virtual PC as a (thin as possible) software RAID layer between the actual hardware and a Win 7 VM.  I'd set it up to just automatically boot to an x window session as the root user and run the VM fullscreen.  Seems like I'd have to have a lot running to get this to work though - Linux, mdadm, x windows, networking, more(?) - and I have no idea what the overhead would actually be or if it'd actually be worth it in the end.

Ideally the Linux install would be as minimalistic as possible and just pass as much access to the hardware down to the VM as possible.  So, how well could this work, and how best to set it up and optimize it?  Any thoughts?

---

### Post by zero2xiii on 2011-12-13
Wow,

Hmmm first of all. Most of the performance you might gain trough this, will be lost on virtualization. Since you add a few paths between drive and use.. (SSD and WIN).. 

And you loose more in reality than you do gain. For example, 3D acceleration is not implemented in 99% of virtual machine software I have worked with. So there goes that aswell.

However this is very possible to do, I have 2 servers running similar setups (minus the RAID as i have 4 x 2TB drives in each running 2 x 2 for each virtual OS in a sence)

Maybe someone might be able to asssit you beter, but bare in mind the performance losses you will have due to virtulization. 

Cherz

---

### Post by 4evrplan on 2011-12-13
Hmm.  Well giving up HW acceleration would be a deal breaker.  If only there was a way to put a disk control emulation layer between the hardware and OS without virtualizing.  I guess what would be needed is a custom driver for Windows that supported software RAID and could be loaded during OS installation, but something tells me that will never be an open source project.  Maybe mdadm for Windows?

Any takers? :lol:

---

### Post by zero2xiii on 2011-12-13
Custom or third party drivers sound like the way to go.

I seem to recall during XP install before everything you had the option to hit one of the F* keys to install 3rd party RAID controlers. But that is windows and I haven't dug into the bones of windows since before XP sp3 came out.. Never the less Vista or 7.

Google a bit, or hang around, there might be a skilled windows user that might help you.

GOod luck with that :)

---

