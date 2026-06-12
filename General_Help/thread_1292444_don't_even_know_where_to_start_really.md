---
title: "don't even know where to start really"
date: 2009-10-15
forum: General Help
---

### Post by Chetnik on 2009-10-15
basically, I just installed ubuntu on my Dell XPS desktop, and I'm having some trouble already.

So first off, I have to boot up ubuntu from my flashdrive when ever I want to get on to ubuntu.

Secondly, when I partitioned my first HD, apparently I can't boot up windows, so is there anything I can do along those lines to try to fix that problem?

Also ubuntu won't seem to connect to the internet as well, even though I set the password correct and the connection type correct.

Now normally I don't really have to deal with these types of things because my Mac spoils me, but I figured I would give Ubuntu a shot, and so far I'm pretty overwhelmed, so anything you can do to help me would be great. 

Under Sysem->Partition Device I see
/dev/sda1 file system ext3 size 143.26gb
/dev/sda2 file system extended 
      /dev/sda5 file system linux-swap

so far i'm getting a GRUB Error 2 when loading 

so basically i can use NVIDIA STRIPE which isn't loading up right now 

USB which loads linux fine 

Utility Partition isn't recognizing, says its not available

using Ubuntu newest edition. 9.0.4 i think

---

### Post by sandyd on 2009-10-15
> **Chetnik said:**
> basically, I just installed ubuntu on my Dell XPS desktop, and I'm having some trouble already.

So first off, I have to boot up ubuntu from my flashdrive when ever I want to get on to ubuntu.

Secondly, when I partitioned my first HD, apparently I can't boot up windows, so is there anything I can do along those lines to try to fix that problem?

Also ubuntu won't seem to connect to the internet as well, even though I set the password correct and the connection type correct.

Now normally I don't really have to deal with these types of things because my Mac spoils me, but I figured I would give Ubuntu a shot, and so far I'm pretty overwhelmed, so anything you can do to help me would be great. 

Under Sysem->Partition Device I see
/dev/sda1 file system ext3 size 143.26gb
/dev/sda2 file system extended 
      /dev/sda5 file system linux-swap

so far i'm getting a GRUB Error 2 when loading 

so basically i can use NVIDIA STRIPE which isn't loading up right now 

USB which loads linux fine 

Utility Partition isn't recognizing, says its not available

using Ubuntu newest edition. 9.0.4 i think
lets try this...

on the linux usb, go to Applications -> Accessories -> Terminal

type this in
```

sudo update-grub

```

restart and see if it makes a difference.

if it doesnt, run this
```

sudo gparted

```
right click on sda5 and select swapoff
delete sda1, sda2, and sda5 

then click the install icon on the desktop.

when you get to partitioning, tell ubuntu to use the free space avalible.

---

### Post by Chetnik on 2009-10-15
> **carlee said:**
> lets try this...

on the linux usb, go to Applications -> Accessories -> Terminal

type this in
```

sudo update-grub

```restart and see if it makes a difference.

if it doesnt, run this
```

sudo gparted

```right click on sda5 and select swapoff
delete sda1, sda2, and sda5 

then click the install icon on the desktop.

when you get to partitioning, tell ubuntu to use the free space avalible.

When you say use the free space available, do you mean larges continuous free space? or Entire disk? 

Everything went well on the other things, I'm paused at this point though

---

### Post by lisati on 2009-10-15
> **Chetnik said:**
> When you say use the free space available, do you mean larges continuous free space? or Entire disk? 

Everything went well on the other things, I'm paused at this point though

"Largest continuous free space" is usually safest, and least likely to hurt other OSes you might have installed on your system.

---

### Post by tgalati4 on 2009-10-15
Well, unless you have another hardisk (labeled probably /dev/sdb1 NTFS), then it looks like you wiped out your windows.  Normally that is a Good Thing(TM).

If you manually partitioned your hard drive, then it looks like you started from scratch, wiping windows off of the drive.  If you use "guided partitioning" it walks you through shrinking the existing windows partition.  I assume this is what you wanted.

---

### Post by Chetnik on 2009-10-15
> **tgalati4 said:**
> Well, unless you have another hardisk (labeled probably /dev/sdb1 NTFS), then it looks like you wiped out your windows.  Normally that is a Good Thing(TM).

If you manually partitioned your hard drive, then it looks like you started from scratch, wiping windows off of the drive.  If you use "guided partitioning" it walks you through shrinking the existing windows partition.  I assume this is what you wanted.

I did not manually partition my HD, Ubuntu did the drive. The guided one would have been nice, but I might have to get Win 7 if this doesn't work out.

It's installing right now, so I hope it works right!

---

### Post by Chetnik on 2009-10-15
Nope, same thing. I'm still having to boot up through my USB drive

---

