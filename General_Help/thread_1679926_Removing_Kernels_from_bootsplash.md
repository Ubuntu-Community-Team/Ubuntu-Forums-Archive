---
title: "Removing Kernels from bootsplash"
date: 2011-02-01
forum: General Help
---

### Post by tam2tam on 2011-02-01
:lolflag:

Okay I have been running Ubuntu for soma months now and it is nice, but now after updating the kernels to get the latest when prompted by the update manager, I now find I have multiple kernels when I boot he PC. My Slackware and Windows 7 options are way down the list. How do I remove the older options. Idealy I would like just the last two kernels and there safe modes on display as options.

Any ideas?

---

### Post by plucky on 2011-02-01
> **tam2tam said:**
> :lolflag:

Okay I have been running Ubuntu for soma months now and it is nice, but now after updating the kernels to get the latest when prompted by the update manager, I now find I have multiple kernels when I boot he PC. My Slackware and Windows 7 options are way down the list. How do I remove the older options. Idealy I would like just the last two kernels and there safe modes on display as options.

Any ideas?

Open **Synaptic Package Manager** and search for **linux-image** and **linux-headers** and mark for complete removal for the older kernels.

Make sure you don't select the current kernel and headers.Also a good idea to keep at least one older kernel.

Good Luck

---

### Post by quadproc on 2011-02-01
> **tam2tam said:**
> :lolflag:

Okay I have been running Ubuntu for soma months now and it is nice, but now after updating the kernels to get the latest when prompted by the update manager, I now find I have multiple kernels when I boot he PC. My Slackware and Windows 7 options are way down the list. How do I remove the older options. Idealy I would like just the last two kernels and there safe modes on display as options.

Any ideas?
The selections displayed are offered by grub, the bootloader.  There are actually two different grubs: the original which was just called grub, and the new one which is known as grub 2 or as grub-pc.  You will need to know which one you are using because they work in different ways.

What I am writing will apply to grub-pc, the later one.

There are several ways to delete operating systems from grub-pc's notice.  One is to mark the unwanted kernel's file permissions not executable.  Another is to actually remove the undesired kernel and probably the best way to do that is with Synaptic, or with apt-get.  Whichever method you choose, you will need to run sudo update-grub afterwards; this will create a new grub.cfg file from the eligible kernels and memtests.

There is a very good writeup on using grub-pc and grub at [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

quadproc

---

