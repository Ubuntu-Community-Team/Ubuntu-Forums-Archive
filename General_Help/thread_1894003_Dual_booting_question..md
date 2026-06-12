---
title: "Dual booting question."
date: 2011-12-11
forum: General Help
---

### Post by AaronDaycentChild on 2011-12-11
So I have ubuntu 11.10 running on my laptop, but unfortunately I need the use of windows 7 for this recording software that I've just ordered. Now I know when you install ubuntu in the beginning it gives you the option to keep a separate partition for you to keep windows on, but I deleted it when I switched to ubuntu because I had no need for it. 

The question is: How would I create a separate partition to run windows on? Just like a dual booting machine.

Also, would it be wise to get a torrented copy of windows for this dual boot?

---

### Post by batharoy on 2011-12-11
Use Gparted to shrink the current partition then format the unallocated space for windows.

---

### Post by AaronDaycentChild on 2011-12-11
> **batharoy said:**
> Use Gparted to shrink the current partition then format the unallocated space for windows.

And then I can just follow the regular install procedure for windows? All I have to do is select that partition to install on?

---

### Post by batharoy on 2011-12-11
Yes. But remember that windows will over write the boot sector so you will have to re-install grub.

---

### Post by AaronDaycentChild on 2011-12-11
> **batharoy said:**
> Yes. But remember that windows will over write the boot sector so you will have to re-install grub.

Damn, and that can be acquired in the software centre?

---

### Post by batharoy on 2011-12-11
Instructions for re-installing grub
[http://www.lancelhoff.com/restore-grub2-after-installing-windows/]("http://www.lancelhoff.com/restore-grub2-after-installing-windows/")

---

### Post by AaronDaycentChild on 2011-12-11
> **batharoy said:**
> Instructions for re-installing grub
[http://www.lancelhoff.com/restore-grub2-after-installing-windows/]("http://www.lancelhoff.com/restore-grub2-after-installing-windows/")

Thanks! This is exactly what I wanted. :KS

---

### Post by Mark Phelps on 2011-12-12
> **AaronDaycentChild said:**
> Also, would it be wise to get a torrented copy of windows for this dual boot?

Why are you going after a "torrented copy"?  Do you not have a legal copy, or access to the official MS downloads?

---

### Post by soap1 on 2011-12-12
instead of partitioning your hard drive and installing windows you could just install wine and run the windows program through that.  Alternatively, you could install windows as a virtual machine.

---

### Post by AaronDaycentChild on 2011-12-13
> **Mark Phelps said:**
> Why are you going after a "torrented copy"?  Do you not have a legal copy, or access to the official MS downloads?

I don't have a legal copy. When I bought this laptop it came with Windows 7 pre-installed, with no disk. 

And I do not have the cash for windows 7, nor would I pay such a high price for such an awful OS, but unfortunately I need it, and it's the best Windows OS out there, in my opinion.

> **soap1 said:**
> instead of partitioning your hard drive and installing windows you could just install wine and run the windows program through that.  Alternatively, you could install windows as a virtual machine.

I find running programs through wine to be an absolute pain in the ***. I installed "Elder Scrolls: Oblivion" but it just will not play.

And I'd rather be able to boot into a fully operational OS rather than just using a virtual machine, which I find has lesser functionalities, e.g. the inability the desktop make it full screen.

---

### Post by dragonfly41 on 2011-12-13
As a long shot .. do you still have a partition called "Recovery" ?

I don't have Windows 7 myself (too pricey) .. but my Vista came as bundled OEM with a Recovery partition which allows Vista to be reinstalled as a factory default.

Can you reinstall Windows factory default from this partition (if it is still there)?

There is a Windows 7 recovery disk you can download.

---

### Post by AaronDaycentChild on 2011-12-17
> **dragonfly41 said:**
> As a long shot .. do you still have a partition called "Recovery" ?

I don't have Windows 7 myself (too pricey) .. but my Vista came as bundled OEM with a Recovery partition which allows Vista to be reinstalled as a factory default.

Can you reinstall Windows factory default from this partition (if it is still there)?

There is a Windows 7 recovery disk you can download.

I don't have that at all. I did not know about that feature. I just downloaded a copy of windows today. I'm currently installing it on Virtual Box, and everything is installing as expected.

---

