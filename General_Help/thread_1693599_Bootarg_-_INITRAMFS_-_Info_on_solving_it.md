---
title: "Bootarg - INITRAMFS - Info on solving it"
date: 2011-02-23
forum: General Help
---

### Post by NicoPapa on 2011-02-23
Hi all, 

I am new here, and have been using Ubuntu since last August (6motnhs now) from a USB key and the an external SSD drive ;) It ROCKS as hell on any computer, including my DELL latitude D830.

Nevertheless, I wanted to share with you a problem I regularly have concerning Ubuntu. And a potential solution I found working for me.

I randomly get the very upsetting "no init found, trying to pass Bootarg" and then the initramfs stuff.

It turns out that I have got over it 3 times now. First time by using Testdisk from a live cd version of Ubuntu. The second, using twice the recuperation mode (which in my opinion did not help) and launching an older version of the kernel from my grub interface. It started ubuntu regularly and ask for a dickcheck, and then if I wanted to try and repair the errors found (push F to repair the errors -something liek that).

And this happened once again, no later than today, 10 minutes ago. I directly booted from an older kernel version which would directly launch the disk checking procedure.
And it works, as you can see.

I wanted to share with you this info, because I have been looking a lot through these forums to solve that problem.

My grub has three ubuntu kernel to propose (I have not done anything for it, it just did it automatically after the upgrades), and windows. The latest ubuntu has a kernel number finishing by 32 (I believe). A previous one finishing with 28, and the last one which saves me after this initramfs trouble, finishing with 26.   They are all from the 10.04 version (lucid lynx right?).

I'll complete the thread with the exact infos on the kernel proposed by grub.

A subsidiary question is:
Why does the older kernel starts normally and even launches a checking of the disk, and not the new version of the kernel ? Why the new version of the kernel does not recongnize that a checking is needed and corrects the mistake ?


Best regards to you all

---

### Post by NicoPapa on 2011-02-23
Corrections made concerning the kerneml available from my Grub

2.6-32-28 (generic)
2.6.32-24 (generic)
2.6.32-21 (generic)

The 32-21 version works when I got some intiramfs appearing on my screen.

---

