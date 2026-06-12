---
title: "lucid boots to initramfs, can &quot;return&quot; to desktop?"
date: 2011-12-25
forum: General Help
---

### Post by kurja on 2011-12-25
When I power on the computer, Ubuntu Lucid boots to initramfs prompt, if I reboot or type command ```
return
``` my gui desktop comes up as usual. This happens every time I power up the pc. Any ideas on what might cause the problem?

---

### Post by West201 on 2011-12-25
Can you post your grub.conf file ? 

I believe it's located in /boot/grub/

---

### Post by BC59 on 2011-12-25
Look here if you can do something.
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)
In any case there is no easy solution.

---

### Post by kurja on 2011-12-25
> **jessejj89 said:**
> Can you post your grub.conf file ? 

I believe it's located in /boot/grub/

update: it does *not* happen every time, I just powered up and got directly to my ubuntu desktop.

I believe you mean grub.cfg? It's in the attached .zip (apparently I can't attach a dot cfg file).

---

### Post by kurja on 2011-12-25
> **BC59 said:**
> Look here if you can do something.
[http://smartmontools.sourceforge.net/badblockhowto.html](http://smartmontools.sourceforge.net/badblockhowto.html)
In any case there is no easy solution.

If I understand correctly you believe this is a disk issue? This computer is booting from a three week old ssd. Of course that doesn't mean that it would work flawlessly, but anyway.

---

### Post by matt_symes on 2011-12-25
Hi

Turn on debugging in initramfs and plymouth.

You need to add the lines

```
debug plymouth:debug
```to the kernel command line. You can do this from the grub screen by selecting your kernel and pressing a key it edit it. It will not persist after reboot.

When you boot you will see a lot more information on the screen and there will also be a symbolic link to the log file in /dev/.initramfs. It's just a simple of what the scripts are doing.

You can also check dmesg.

Post back all of them here between code tags.

It may be as simple as increasing the root delay for the SSD.

Kind regards

---

### Post by kurja on 2011-12-26
> **matt_symes said:**
> Hi

Turn on debugging in initramfs and plymouth.

You need to add the lines

```
debug plymouth:debug
```to the kernel command line. You can do this from the grub screen by selecting your kernel and pressing a key it edit it. It will not persist after reboot.

When you boot you will see a lot more information on the screen and there will also be a symbolic link to the log file in /dev/.initramfs. It's just a simple of what the scripts are doing.

You can also check dmesg.

Post back all of them here between code tags.

It may be as simple as increasing the root delay for the SSD.

Kind regards

I found this in dmesg: ```
[    7.136020] ata2: link is slow to respond, please be patient (ready=-19)
[   11.840012] ata2: device not ready (errno=-16), forcing hardreset
[   17.036016] ata2: link is slow to respond, please be patient (ready=-19)
[   21.852019] ata2: SRST failed (errno=-16)
[   27.048016] ata2: link is slow to respond, please be patient (ready=-19)
[   31.864029] ata2: SRST failed (errno=-16)
[   37.060017] ata2: link is slow to respond, please be patient (ready=-19)
[   66.908016] ata2: SRST failed (errno=-16)
[   66.908021] ata2: limiting SATA link speed to 1.5 Gbps
[   71.936016] ata2: SRST failed (errno=-16)
[   71.936019] ata2: reset failed, giving up
```

and I have had recent issues with the second disk, hmm.

I'll post other debug info later.

---

### Post by matt_symes on 2011-12-26
Hi

Try increasing your rootdelay parameter in the kernel command line.

Go with something like ```
rootdelay=90
``` and see how that takes you.

Although, in this case, i am not sure it would fix your problem.

Kind regard

---

### Post by kurja on 2011-12-29
Thanks for your help everyone, it appears that the problem was created by a failing second hard drive. I've now replaced that and the problem has not occurred since.

---

