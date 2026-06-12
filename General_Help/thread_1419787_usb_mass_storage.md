---
title: "usb mass storage"
date: 2010-03-02
forum: General Help
---

### Post by Bob King on 2010-03-02
I am using Ubuntu 9.10 and until recently USB memory sticks and usb external HDD were instantly recognized and mounted.  I must have done something silly because now memory sticks are not recognized until I open 'USB startup disk creator' and external HDD is not accessible at all.  If I try to mount  the memory stick manually in Terminal it returns:
'Cannot mount because sdb# cannot be found in fstab or mtab', or similar.

Can anyone help please before I get carted away to the looney bin?

[Laptop Fujitsu Amilo Pi1505 AMD64 if this is relevant]

Bob

---

### Post by Elwro on 2010-03-02
I had a similar problem with automount and described it in [this thread](http://ubuntuforums.org/showthread.php?t=1418134). The solution linked to in [this](http://ubuntuforums.org/showpost.php?p=8903538&postcount=11) post worked for me, but as you will see if you read that thread it might be risky.

---

### Post by Bob King on 2010-03-03
> **Elwro said:**
> I had a similar problem with automount and described it in [this thread](http://ubuntuforums.org/showthread.php?t=1418134). The solution linked to in [this](http://ubuntuforums.org/showpost.php?p=8903538&postcount=11) post worked for me, but as you will see if you read that thread it might be risky.
Thanks Elwro.  My problem is not automount but no mount at all.  The USB storage does not appear in fstab or mtab so cannot mount.  I installed 9.10 on another HDD and no problem with USB but other programs didn't work.  I think I will take Keir Thomas' advice and install 32 bit instead of 64.
USB startup disk creator enables the use of USB memory stick but doesn't mount it.
When I ask for 'unmount' after using the stick it says it can't unmount.
Looks like 9.10 has some odd effects.
Bob

---

### Post by fluffman86 on 2010-03-03
switching to 32bit won't make a bit of difference, other than you're getting a fresh install. I've had problems with mounting before, but nothing explicitly related to running 64bit.

---

### Post by QLee on 2010-03-03
[QUOTE=Bob King]  The USB storage does not appear in fstab or mtab so cannot mount. [/QUOTE]

Just to clarify, what you put in fstab is for what you want mounted at boot time and non-auto mounted devices that you want to use a shortened form of the path when manually mounting from the command line. You'd only want a USB drive automounted from fstab if it was always connected at boot time. and, they aren't in mtab until they are mounted.

Can you manually mount the drive?

[QUOTE=Bob King]Looks like 9.10 has some odd effects.[/QUOTE]

It likely is some configuration issue, 9.10 works well here and I've even upgraded a 9.10 install to 10 alpha 3 and it works well too

---

