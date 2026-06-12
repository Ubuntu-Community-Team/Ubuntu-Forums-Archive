---
title: "CD/DVD drive not recognised"
date: 2011-08-10
forum: General Help
---

### Post by ibates on 2011-08-10
I suspect this is a dead horse which has been flogged to death many times.  But if it has, solutions to the threads are well disguised and I can not find them.

I am running Ubuntu 10.04.03 on an ASUS P5VD2-X.  There are numerous HDD attached, but one is uniquely Win XP, the other uniquely Ubuntu.  Boot choice is via a GRUB loader.  Ubuntu is the first choice normally.

The problem is that more often than not, the system does not seem to be able to recognise the CD or DVD reader/writer.  On some random occasions, they are recognised, but mostly not.

But - and here is the upsetting bit - this problem ***never*** occurs when I boot up on Win XP.  The CD/DVD devices are instantly and reliably recognised each and every time.

So I guess that rules out a hardware or BIOS problem.

This is a particularly annoying problem as use of the optical drives is required frequently, and it galls me having to revert to Windows just to use them.

What is going on?  Can anyone help solve this annoying problem?

---

### Post by dcstar on 2011-08-10
> **ibates said:**
> I suspect this is a dead horse which has been flogged to death many times.  But if it has, solutions to the threads are well disguised and I can not find them.

I am running Ubuntu 10.04.03 on an ASUS P5VD2-X.  There are numerous HDD attached, but one is uniquely Win XP, the other uniquely Ubuntu.  Boot choice is via a GRUB loader.  Ubuntu is the first choice normally.

The problem is that more often than not, the system does not seem to be able to recognise the CD or DVD reader/writer.  On some random occasions, they are recognised, but mostly not.

But - and here is the upsetting bit - this problem ***never*** occurs when I boot up on Win XP.  The CD/DVD devices are instantly and reliably recognised each and every time.

So I guess that rules out a hardware or BIOS problem.

This is a particularly annoying problem as use of the optical drives is required frequently, and it galls me having to revert to Windows just to use them.

What is going on?  Can anyone help solve this annoying problem?

If the drives are on IDE connections, make 100% sure the Master and Slave jumpers are set correctly and do not have only a Slave device on an IDE channel.

---

### Post by ibates on 2012-01-17
Thank you for the hint David.  I had never considered reassessing jumper settings, probably because the problem had not manifested itself when running Windows.

When I first installed these two devices, I was advised, by I remember not whom, to set the jumpers for Cable Select.  This, it appears, might not have been good advice.

The jumpers have now been set for Master and Slave respectively, and following lots of testing, the problem seems to have disappeared.

Thank you once again.

---

