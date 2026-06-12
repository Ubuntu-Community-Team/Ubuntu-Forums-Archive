---
title: "Ubuntu completely locks up, needs hard reset"
date: 2012-07-20
forum: General Help
---

### Post by ashughes on 2012-07-20
I recently installed Ubuntu 12.04 64-bit on my new Lenovo Thinkpad X230. I've noticed that it completely hangs intermittently. I suspect a kernel hang because CTRL+ALT+DEL, CTRL+ALT+BACKSPACE, ALT+F1, ALT+F2, nor CTRL+ALT+REISUB works to restore functionality. The only thing that works is a hard reboot.

I have a desktop computer at home running Ubuntu 12.04 and it does not experience this problem, so I think it's something unique to this machine. The only difference I can see is that on my laptop, I have a wireless USB mouse and a USB hard drive.

I noticed that the "crash" is usually preceded by me moving my mouse, but I can be working for a full day sometimes before it crashes.

I also noticed today that my USB hard drive was mounted and dismounted randomly while I was using it. Could it be faulty USB ports causing a kernel panic? 

One final point, I'm running Ubunut's home folder encryption on my laptop, but not on my Desktop. Might that make a difference? Are there known issues related to drive encryption?

Thanks in advance.

---

### Post by moore.bryan on 2012-07-20
Have you gone back and looked at your dmesg?

---

### Post by ashughes on 2012-07-20
I just checked dmesg and nothing stands out to me. Is there something I should be looking for?

---

### Post by fellgrail on 2012-07-22
upgrade your kernel to 3.3 I think - whatever the latest one is (not yet in repos). I found that solution in another post.

---

