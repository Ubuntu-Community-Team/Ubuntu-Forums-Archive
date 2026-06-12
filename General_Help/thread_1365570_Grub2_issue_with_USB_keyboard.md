---
title: "Grub2 issue with USB keyboard"
date: 2009-12-27
forum: General Help
---

### Post by zetazot on 2009-12-27
I've just installed 9.10 and upgraded it to Ubuntu Studio via the terminal. This was a fresh install. Ubuntu is the only thing on this hard drive. Once I got it up and running, I plugged in my Windows XP hard drive and configured grub to recognise it.

When I rebooted, Grub gave me the list with all the Ubuntu options and Windows XP last. I wanted to test Windows out so I tried to use the arrow keys on my USB keyboard. It wouldn't work. My mouse was not lit up either, so none of my USB devices are getting power.

I plugged in an old and semi-functional PS2 keyboard and it worked fine.

Is there anyway to get the USB keyboard to work with Grub2?

Thanks in advance!

---

### Post by zetazot on 2009-12-27
Did a little digging... Enabling USB support in the BIOS made a world of difference.

So its solved. Thanks for looking!

---

### Post by dcstar on 2009-12-27
> **zetazot said:**
> Did a little digging... Enabling USB support in the BIOS made a world of difference.

So its solved. Thanks for looking!

Good work on finding your own solution, now have a look at the info in my sig:

---

