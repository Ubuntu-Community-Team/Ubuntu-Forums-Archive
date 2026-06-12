---
title: "Hibernation is gone"
date: 2010-06-04
forum: General Help
---

### Post by lanig on 2010-06-04
Hi all,

A few days ago, after I made some changes on my lucid system, hibernation is not possible any more, that is, if I choose hibernation, everything seems to go fine but at the next boot, the image is not read by the kernel and normal boot happens.

Hibernation is very important to me,  what can I do go get it back ?

TIA

Alain

---

### Post by dcstar on 2010-06-05
> **lanig said:**
> Hi all,

A few days ago, after I made some changes on my lucid system, hibernation is not possible any more, that is, if I choose hibernation, everything seems to go fine but at the next boot, the image is not read by the kernel and normal boot happens.

Hibernation is very important to me,  what can I do go get it back ?

TIA

Alain

Spin on your head three times?

Actually, tell us some of the changes **you** made and it might just provide some information to help your situation.

---

### Post by lanig on 2010-06-05
Hi, 
Thanks for your answer.
I did several things at the same time.
First did most of the modificiations listed[there]("http://doc.ubuntu-fr.org/services") in the "Services propres aux PCs portable" (laptop specific services", sudo update-rc.d -f apmd remove.

At the same time, I had to reinstall windows and then reinstall grub from the live cd. During this time, I resized some partitions (including my swap partition) and plugged in an IDE disk.

I have already tried to apt-get remove --purge pm-utils ; apt-get install acpi-support pm-utils pm-utils-powersave-policy with no success.

Alain

---

### Post by lanig on 2010-06-05
Found out a solution 
added resume=/dev/sdb6 to menu.lst
but it is not quite satisfying : I have used hibernation for years without having to modify the menu.lst.

---

