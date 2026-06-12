---
title: "USB Stick"
date: 2012-01-24
forum: General Help
---

### Post by Gwaro on 2012-01-24
Does everybody have this problem with USB drives,whereby when copying content to it takes very long? The copying speed also behaves weirdly, very fast at first but then slows. All this time, the system keeps freezing and refreezing! Any workarounds?
This is my only setback in Ubuntu.

---

### Post by sudodus on 2012-01-24
It is common that writing is slow with USB sticks. Sometimes also reading is slow. Some sticks are faster than others, and you can select a fast one next time you buy a stick. There are USB 3 sticks now that are really fast, (also faster than standard sticks, when using the USB 2.0 interface).

I think that the copying seems fast in the beginning, because it writes into a RAM buffer. Some sticks have a light emitting diode, that shows the read/write activity, and you can see that it is busy after the application program shows that the copying has finished.

I have also noted that it is very slow copying many small files compared to writing the same amount as one big file, so it is worth considering making a tar archive file or a tar-gzip compressed archive 'tarball' to backup or move a lot of small files.

*Edit: But my system does not freeze because of slow communication with the USB stick.*

---

### Post by 3rdalbum on 2012-01-24
> **Gwaro said:**
> Does everybody have this problem with USB drives,whereby when copying content to it takes very long? The copying speed also behaves weirdly, very fast at first but then slows. All this time, the system keeps freezing and refreezing! Any workarounds?
This is my only setback in Ubuntu.

This behaviour sounds like the USB drive is formatted as NTFS.

NTFS writing is slow because it is CPU-bound on Linux. If you reformat the USB stick to Ext4 or vfat you'll get "native" speed transfers with no "freezing", and it won't put load on your CPU.

---

### Post by Gwaro on 2012-01-27
> **3rdalbum said:**
> This behaviour sounds like the USB drive is formatted as NTFS.

NTFS writing is slow because it is CPU-bound on Linux. If you reformat the USB stick to Ext4 or vfat you'll get "native" speed transfers with no "freezing", and it won't put load on your CPU.


I tried Ext4 but the situation is same.

---

### Post by Gwaro on 2012-01-27
> **Gwaro said:**
> Does everybody have this problem with USB drives,whereby when copying content to it takes very long? The copying speed also behaves weirdly, very fast at first but then slows. All this time, the system keeps freezing and refreezing! Any workarounds?
This is my only setback in Ubuntu.


I noticed 11.04 was better on this.

---

### Post by sudodus on 2012-01-27
> **Gwaro said:**
> I noticed 11.04 was better on this.
Then I think you can test if the computer is simply too busy.

Sometimes the communication with the graphics card or chip does not work well. For example, if you have an nvidia card, you need a proprietary driver (and you should be offered automatically by the system to install it). Then the whole computer will start to run faster. Even things not related to the graphics will run faster, because the communication channels in the motherboard will no longer be busy with the graphics. At least this is how I think it can be described. It may be similar if you have an ATI card.

If you cannot make it work well enough with a proprietary graphics driver, an alternative might be to use a light-weight flavour of Ubuntu. Lubuntu with LXDE has the smallest footprint, and Xubuntu with XFCE has a small footprint too. So download the iso files and make bootable CD or USB drives and test the systems live.

But to be able to give more precise advice, please let us know what computer it is: CPU, RAM, graphics card or chip.

---

### Post by Gwaro on 2012-01-30
> **sudodus said:**
> Then I think you can test if the computer is simply too busy.

Sometimes the communication with the graphics card or chip does not work well. For example, if you have an nvidia card, you need a proprietary driver (and you should be offered automatically by the system to install it). Then the whole computer will start to run faster. Even things not related to the graphics will run faster, because the communication channels in the motherboard will no longer be busy with the graphics. At least this is how I think it can be described. It may be similar if you have an ATI card.

If you cannot make it work well enough with a proprietary graphics driver, an alternative might be to use a light-weight flavour of Ubuntu. Lubuntu with LXDE has the smallest footprint, and Xubuntu with XFCE has a small footprint too. So download the iso files and make bootable CD or USB drives and test the systems live.

But to be able to give more precise advice, please let us know what computer it is: CPU, RAM, graphics card or chip.

Intel core 2 Duo CPU T6570 @ 2.10GHz x 2, RAM 1.9 GiB, Graphics Mobile Intel GM45 Express Chipset

---

### Post by sudodus on 2012-01-30
> **Gwaro said:**
> Intel core 2 Duo CPU T6570 @ 2.10GHz x 2, RAM 1.9 GiB, Graphics Mobile Intel GM45 Express Chipset
Your computer should have muscles enough to run the new Ubuntu 11.10. However there might be something (bug or driver that does not fit your hardware), that makes it slow. Since you 'noticed 11.04 was better on this', it might be a good idea to go back to that version of Ubuntu and wait until things are improved in a later update of 11.10 or the new long time support version 12.04, that will be released in April.

So, when you feel like it, download the current version and test it live, booted from a CD or USB drive, to find out that it works properly before installing or upgrading.

---

### Post by Gwaro on 2012-01-31
> **sudodus said:**
> Your computer should have muscles enough to run the new Ubuntu 11.10. However there might be something (bug or driver that does not fit your hardware), that makes it slow. Since you 'noticed 11.04 was better on this', it might be a good idea to go back to that version of Ubuntu and wait until things are improved in a later update of 11.10 or the new long time support version 12.04, that will be released in April.

So, when you feel like it, download the current version and test it live, booted from a CD or USB drive, to find out that it works properly before installing or upgrading.


Thank you. I will try that.

---

