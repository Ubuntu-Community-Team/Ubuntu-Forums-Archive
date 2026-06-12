---
title: "Format a hard drive"
date: 2009-11-16
forum: General Help
---

### Post by waltwin on 2009-11-16
I want to format my hard drive in my computer. I understand that if I install a fresh copy of ubuntu 9.04 it will format the drive. My problem I have also installed 9.04 on a second hard drive and I want to format that drive also.

I have tried the new 9.10 but it slowed my machine to a crawl.

When I start my machine it offers several kernels to select from and I don't know what one I want.

I did get one answer stating that I should "Use gparted from the live cd" but I can't understand what that means. I installed the "live cd" that holds 9.04 but I don't see it there as an option.

Where is "gparted"?

Thank you 

waltwin

---

### Post by audiomick on 2009-11-16
Hallo.
What they're talking about is not installing, but rather booting from the live cd. When you start the computer with the cd in the drive, assuming the computer knows to look for the cd/dvd drive when it is booting, the cd starts and offers you the option of starting Ubuntu without changing the computer. When you select that, Ubuntu loads into the RAM, and you have a running Ubuntu without actually having installed it.
When you hve done that, go to the system administration menu and look for the partition editor ( gparted ).
Gparted is a tool for manipulating partions on you hard drives. When you start it, it should find all the drives that are in the computer, and allow you to re-partition / format them. 

Also: If you just run the installer, it will also find all the drives in the computer. If you then chose the manual option to do the partitions, you can tell it to format and partition all the discs as you wish.

---

### Post by waltwin on 2009-11-16
> **audiomick said:**
> Hallo.
What they're talking about is not installing, but rather booting from the live cd. When you start the computer with the cd in the drive, assuming the computer knows to look for the cd/dvd drive when it is booting, the cd starts and offers you the option of starting Ubuntu without changing the computer. When you select that, Ubuntu loads into the RAM, and you have a running Ubuntu without actually having installed it.
When you hve done that, go to the system administration menu and look for the partition editor ( gparted ).
Gparted is a tool for manipulating partions on you hard drives. When you start it, it should find all the drives that are in the computer, and allow you to re-partition / format them. 

Also: If you just run the installer, it will also find all the drives in the computer. If you then chose the manual option to do the partitions, you can tell it to format and partition all the discs as you wish.
Thank you very much.I think that I have a better understanding of what to do. I guess that you have figured out that I am new at this.

waltwin

---

### Post by audiomick on 2009-11-16
good luck and have fun;)

---

### Post by waltwin on 2009-11-16
I just wanted to say that your instructions were spot on and I been able to accomplish what I wanted to do.

Thank you again

waltwin

---

