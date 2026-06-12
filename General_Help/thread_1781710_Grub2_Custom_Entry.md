---
title: "Grub2 Custom Entry"
date: 2011-06-13
forum: General Help
---

### Post by JimmyJoeBob on 2011-06-13
Hello,

I recently decided to play around with Gentoo, but I wanted to keep Ubuntu as my main OS.  I had an extra hard drive, so I just put Gentoo on there.  However, I'm having some trouble with Grub2.  I decided not to install any kind of bootloader on the Gentoo drive because I plan to keep using Ubuntu most of the time.  I figured I could just add a menu entry to the Grub2 install that Ubuntu set up.  My first instinct was to just use update-grub, since that worked fine for my Windows install.  Unfortunately, update-grub finds the Gentoo kernel, but it doesn't show up when I reboot, so I figured I would have to write a custom menu entry in /etc/grub.d/40_custom or something.

Here's the problem: in keeping with the Gentoo install guide, I put /boot in it's own partition, and now I'm either getting a kernel panic because / can't be found, or Grub2 can't find the kernel image.

Here's my partition layout:

(hd0,1) -> Ubuntu /
(hd1,1) -> Gentoo /boot/
(hd1,3) -> Gentoo /

How do I write a Grub2 custom menu entry to boot this configuration? Thanks in advance.

---

### Post by JimmyJoeBob on 2011-06-14
Turns out I had a kernel config problem.  Using:

set root=(hd1,1)
linux /kernel-2.6.xx root=/dev/sdb3

works fine in case others are wondering.

---

### Post by wildmanne39 on 2011-06-14
> **JimmyJoeBob said:**
> Turns out I had a kernel config problem.  Using:

set root=(hd1,1)
linux /kernel-2.6.xx root=/dev/sdb3

works fine in case others are wondering.
Hi, glad you got it fixed and thank you for posting the answer.

---

