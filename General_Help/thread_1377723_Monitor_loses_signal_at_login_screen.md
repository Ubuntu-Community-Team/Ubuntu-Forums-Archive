---
title: "Monitor loses signal at login screen"
date: 2010-01-10
forum: General Help
---

### Post by glopso on 2010-01-10
I have Ubuntu Linux 9.10 (I think it's called Karmic Koala or something) and the latest Nvidia graphics card driver (for my graphics card).
 
The problem:
I can start up the computer. The bios stuff pops up, then it shows the grub loading fine, then the boot from hard drive 0  stuff, and then the circle with the dots(I never bothered to learn what that's supposed to be). But when it's supposed to go to the login screen, my monitor loses focus! I'm sure it has something to do with the monitor or graphics card, and not the computer hanging. I know it isn't hanging because when I press the power button and press enter the computer turns off.
 
The first time this happened was when I got a new driver for the graphics card. This was a few months ago. After I changed my usb mouse with a mouse with the older kind of mouse port mouse, it started acting up again. I'm pretty sure that the mouse isn't the problem, just thought I should mention it.

---

### Post by glopso on 2010-01-10
Maybe I just posted at the wrong time and my thread got pushed down. Maybe people just don't care. But I'm BUMPing this anyway.
 
EDIT: I guess noone cares, because the above post alrady has 54 views and I have none

---

### Post by glopso on 2010-01-10
Why doesn't anyone care about me?

---

### Post by howefield on 2010-01-10
> **glopso said:**
> Why doesn't anyone care about me?

Is there a reason why they should ?

Only jesting, but you are deluding yourself if you think posters here are deliberately holding back on you by not offering help when they can.

It is more likely that no one that has read your post knows the answer in the few minutes since you posted your original post.

---

### Post by JDorfler on 2010-01-10
Having the same issue when I upgraded my kernel to the -18.  I just scrolled down in grub to the -17 and rolled on.  Try an older Kernel version.

---

### Post by chousho on 2010-01-10
I'm having a similar problem, actually.

Upon upgrading to 9.10, I've found that it will show the grub menu fine, but after loading whatever kernel is latest (or any) that getting to the login screen will take around half an hour to show.

At first I thought that perhaps my monitor was shut off, or that there was some other issue, however it will get to the login screen... just that it will take literally 30 or so minutes to get there.

I thought this might be due to it doing a file check on my 1TB hdd, which would take a while. However I still experience this huge delay like you're getting.

To save time, I don't select the latest kernel, but the option below and boot as root with network, then su as my user and startx. It's crappy but it gets me online (albeit without a bunch of the perks).

Perhaps this extra information could spark someone's knowledge, if anyone might be able to help us?

---

