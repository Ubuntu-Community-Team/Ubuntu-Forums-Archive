---
title: "Windows XP partition cannot mount."
date: 2009-07-09
forum: General Help
---

### Post by dragos240 on 2009-07-09
Hi,

A poster in my topic, about finding out the problem for windows not booting, told me to try booting into the first partition where the "recovery" tool was located, when booted I accidentally pressed the next button, and now I can't even access my files when I try mounting them. Even when I force them. Rita, a person here, likes playing games such as jewel quest and others. She really doesn't have any other hobbies and gets very angry when things don't go her way. What are some suggestions that I can do to fix this, I fixed it as much as possible with testdisk.

---

### Post by merlinus on 2009-07-09
Photorec is also good for recovering deleted files.

---

### Post by dragos240 on 2009-07-09
> **merlinus said:**
> Photorec is also good for recovering deleted files.

photorec isn't finding any files :sad:

---

### Post by merlinus on 2009-07-09
testdisk may have already recovered everything possible.

---

### Post by graphius on 2009-07-09
Am I following this? You had a windows problem booting, now your windows won't boot?
Can you still boot into Ubuntu?

---

### Post by dragos240 on 2009-07-09
> **graphius said:**
> Am I following this? You had a windows problem booting, now your windows won't boot?
Can you still boot into Ubuntu?

Arch, and yes.

---

### Post by graphius on 2009-07-09
in retrospect, my last post looks a bit snotty, sorry about that...

As to your problem, as others have mentioned it is probably a corrupt or lost file. 
If you are lucky, you might be able to do a repair install of windows, however it might screw up your grub so you wouldn't be able to boot into Ubuntu, you would have to manually fix grub. I did see a how-to somewhere on these forums if it comes to that...
What exactly did you do that stopped Windows booting?

---

### Post by dragos240 on 2009-07-09
> **graphius said:**
> in retrospect, my last post looks a bit snotty, sorry about that...

As to your problem, as others have mentioned it is probably a corrupt or lost file. 
If you are lucky, you might be able to do a repair install of windows, however it might screw up your grub so you wouldn't be able to boot into Ubuntu, you would have to manually fix grub. I did see a how-to somewhere on these forums if it comes to that...
What exactly did you do that stopped Windows booting?

Deleting ubuntu and installing arch.

---

### Post by dragos240 on 2009-07-09
Hello?

---

### Post by graphius on 2009-07-09
I would definitely think it is a grub/lilo issue.
search grub on this forum. As I said, I remember a how-to somewhere
maybe [this]("http://ubuntuforums.org/showthread.php?t=1208920&highlight=grub") thread will help

---

### Post by Eredeath on 2009-07-09
Try using gparted in Arch and making the windows partition bootable. Boot into windows and change the windows boot manager to point to where grub is installed.

---

### Post by dragos240 on 2009-07-09
> **graphius said:**
> I would definitely think it is a grub/lilo issue.
search grub on this forum. As I said, I remember a how-to somewhere
maybe [this]("http://ubuntuforums.org/showthread.php?t=1208920&highlight=grub") thread will help

It isn't. If I can't mount it in arch, I can't boot into it, I erased some of the hard drive by mistake and really need it to be recovered. Please help.

---

### Post by dragos240 on 2009-07-11
**B**ump
**U**p
**M**y
**P**ost

---

### Post by carml on 2009-07-11
Have you got a Recovery Disk of Xp?

---

### Post by dragos240 on 2009-07-11
Yes, It's my last resort.

---

### Post by Eredeath on 2009-07-11
Did you try my idea? I had a problem like this and that is what i did to fix it.

---

