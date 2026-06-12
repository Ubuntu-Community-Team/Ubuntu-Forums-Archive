---
title: "Grub2, vga/gfxpayload (and splashy) problem"
date: 2009-11-11
forum: General Help
---

### Post by M4v3R on 2009-11-11
Hello, I have an uncommon problem with new Ubuntu 9.10. First, some info on what I want to achieve.

I have an old Fujitsu Siemens laptop with 500 MHz CPU that I use for a very specific task. I have an application written in C++/SDL that runs in framebuffer after it starts. There is no X Server on anything because I want it to do only this one thing.

On 9.04, when I had Grub legacy everything was just fine. I've set vga=0x315 mode in kernel line, it booted up in 800x600 mode and then ran my app in this mode. I've also had splashy installed with my custom splash theme so the boot proccess looked nicer.

Now I've decided to make a fresh 9.10 install to benefit from boot speed. In fact, the benefit is great - 20 secs vs 40 secs on 9.04. But I have a problem with video now. It told me that vga is now deprecated and I should use gfxpayload instead. Then I get blank screen - no splash, no nothing. The problem is - gfxpayload doesn't work - it falls back to standard mode without framebuffer enabled.

So my question is - did anyone had a success with setting this new gfxpayload option and/or using splashy under Ubuntu 9.10?

---

