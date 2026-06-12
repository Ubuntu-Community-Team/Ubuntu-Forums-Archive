---
title: "Can't boot liveCD when using Ubuntu."
date: 2011-06-19
forum: General Help
---

### Post by terkelg on 2011-06-19
Hi folks.
This is first post in here and the first time I couldn&#8217;t Google me to an answer.
First of all, I&#8217;m in love with Ubuntu, the Linux spirit and the whole community.  About 2 months ago I made a dual boot with Windwos 7. But after I fell in love with Ubuntu and started learning C, I wanted to remove Windows.

I used the xUbuntu live CD to format all my drives. Wanted to start on a fresh and have a dual boot with Ubuntu and Backtrack 5 instead. I used gParted and it was pretty easy.  Then I installed Ubuntu from the Live CD. Everything went fine. But now when I insert the Backtrack 5 LiveCD (or LiveUSB) it can&#8217;t boot.
The splash screen opens, but whatever I choose it just reboot my machine, which then enter Ubuntu.

I don&#8217;t think its Backtrack, but something with my mbr. But other Live CDs boot just fine. I&#8217;ve tested DamnSmallLinux, xUbuntu and Knoppix. Why can&#8217;t Backtrack boot after I removed Windows, but other liveCD just boot fine?

Can it be something with GRUB? I&#8217;m lost.
Do I really have to install Windows again?

Hope you guys can help me.
Thanks in advance, and sorry my bad English.

---

### Post by ChipOManiac on 2011-06-19
Well... I don't think it's anything to do with the MBR or GRUB... Those things are on your HDD...

---

### Post by terkelg on 2011-06-19
Do you thinks it's Backtrack? But why do I need windows to make it boot. That's wired.

---

### Post by ChipOManiac on 2011-06-19
> **terkelg said:**
> Do you thinks it's Backtrack? But why do I need windows to make it boot. That's wired.

Now that you mention it... yeah that's pretty weird...

---

### Post by Joe- on 2011-06-19
So does the computer actually start to boot from the CD?

---

### Post by jerrrys on 2011-06-19
a live cd boots from your bios and has nothing to do with the hdd.  since you have other cd's that work, just makes me think your disk has gone bad.  got another box you can try that cd in?

---

### Post by terkelg on 2011-06-19
The CD start to boot, and open the Backtrack boot screen too, but when I choose something the machine reboot.
And then I can start over again. Infinite loop.

I'll try on other machines now.

---

### Post by terkelg on 2011-06-19
Before rebooting, Backtrack print these lines:
"Loading /casper/vmlinuz............."
"loading /casper/initrd.gz............."

And shutdown.

---------------------------------
Everything works on my Laptop with XP.

---

