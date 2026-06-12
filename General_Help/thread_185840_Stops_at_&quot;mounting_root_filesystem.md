---
title: "Stops at &quot;mounting root filesystem"
date: 2006-06-01
forum: General Help
---

### Post by fastb on 2006-06-01
Ive just installed the new 606 lts and it can't get pass "mounting root filesysem". If I unplug my USB mouse it gets pass but whats the use if I can't use my mouse. Does anybody know a solution to this problem?
I was so looking forward using the new Ubuntu and now this:(

---

### Post by mostwanted on 2006-06-01
It takes a little while (like 30-40 seconds) to pass that step on my computer. Are you sure you've been patient enough?

Otherwise, isn't it possible to plug in your mouse again after it passes the step?

---

### Post by fastb on 2006-06-01
I've been waiting for at least 15 minutes. If I plug in the mouse once it boots it doesn't recognize it.
The recovery mode doest't boot neither.

---

### Post by maka on 2006-06-01
also if you have any USB drives connected, try disconnecting them before you boot up the system.

i had this identical problem and that fixed it for me.  but i think there are several causes but wont hurt to try.

---

### Post by oppio on 2006-06-16
I've got the same problem after upgrading some packages.
I tried unplugging USB mouse, running evms_activate, changing grub's menu.lst and fstab, and other users' suggestions.... but none seems to work, I always get the message "ALERT! /dev/hdb2 does not exist" and I get dropped to busybox.

I can access everything from LinuxRescueCD so I can change every config file... but I need some advice on what **exactly** should I do...

Any help would be greatly appreciated.
Valerio

---

### Post by Ted_Smith on 2006-06-19
I've written a [HOWTO]("http://www.ubuntuforums.org/showthread.php?t=197956&highlight=ALERT%21") last weekend that will help you.

---

### Post by blimpyboy on 2006-06-19
[QUOTE=fastb]Ive just installed the new 606 lts and it can't get pass "mounting root filesysem". If I unplug my USB mouse it gets pass but whats the use if I can't use my mouse. Does anybody know a solution to this problem?
I was so looking forward using the new Ubuntu and now this:([/QUOTE]

fastb: Could you please try botting with the 23 kernel as opposed to the 25 kernel which came out in an update a few days ago.

I'm having the same problem as you with the 25 kernel.  The 23 kernel works fine.

When you boot with the 25 kernel in recovery mode, do you get an error about 'make_queue' ?  If so , we're in the same boat.

---

### Post by KenF on 2006-10-21
I also have something similar for a few months.  There are several other threads where booting stalls when "mounting root filesystem" and it appears that there are at least 3 different problems occuring.

For mine:
1.  If I unplug my external USB drive before booting there is no problem.
2.  I can boot using an older kernel (2.6.12-9 instead of 2.6.15-23), but I have no sound and there are a few other problems.
3.  I have tried with no success the "UUID solution" presented in other threads.  [The forum moderators generally think this is related to a bug in udev.  I'm convinced this isn't my problem --- mainly because the UUID solution had no effect.]

One thing worth trying is to boot up without the splash screen.  The point is that there are a lot of hardware recognition and device driver loader going on in the section where the splash screen indicates "mounting root filesystem".  [ If you are using grub to boot, you can edit the boot line to delete "quiet" and to change "splash" to "nosplash".]  When I do this, it turns out that my boot stalls at the line where it is trying to register a new USB bus:

Oct 21 15:20:00 localhost kernel: [   22.304793] ACPI: PCI Interrupt Link [LUS0] enabled at IRQ 20
Oct 21 15:20:00 localhost kernel: [   22.304854] GSI 17 sharing vector 0xB9 and IRQ 17
Oct 21 15:20:00 localhost kernel: [   22.304911] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LUS0] -> GSI 20 (level, high) -> IRQ 185
Oct 21 15:20:00 localhost kernel: [   22.305633] ohci_hcd 0000:00:02.0: OHCI Host Controller

Not that this has helped me, but perhaps somebody with more experience can indicate better why it it stalling at this point.  I think I'm going to head back to Breezy.

Thanks,

KenF

---

