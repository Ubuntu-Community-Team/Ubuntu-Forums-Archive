---
title: "ubuntu freezes"
date: 2011-02-16
forum: General Help
---

### Post by philipballew on 2011-02-16
my laptop will about once or twice a week free system wide where the only option is to manually power off. whats a way to find out more about the problem and see exactly whats causing this? i have a dell studio i558 RUNNING 10.10 64 BIT and an 15 proccesor

---

### Post by Rubi1200 on 2011-02-16
What graphics card do you have installed?

If the system freezes and becomes unresponsive, the best way to shutdown or reboot is like this:
[http://kember.net/articles/reisub-the-gentle-linux-restart/](http://kember.net/articles/reisub-the-gentle-linux-restart/)

---

### Post by philipballew on 2011-02-17
```
philip@philip-laptop:~$ lspci | grep -i vga
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18)

```
the next time it does, where in my logs should i look to see if there was a problem there?

---

### Post by Rubi1200 on 2011-02-17
Have you tried booting with the i915.modeset=1 parameter?

Do you have Compiz enabled?

Look in dmesg for signs of freezes etc.

---

### Post by philipballew on 2011-02-17
i do have compez and the whole cube running, i have not changed my boot parameters at all on this machine

---

### Post by Rubi1200 on 2011-02-17
Well, to try and narrow this down first turn Compiz off and see if it helps.

Then, when the computer starts and GRUB comes up highlight the entry for Ubuntu press "e" to edit.

Find the line with quiet splash (use arrow keys to navigate) and append the i915.modeset=1 parameter after quiet splash (with a space between them), then "Ctrl" + "X" to boot.

Might also be worthwhile looking here to try and track things down:
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

### Post by 3rdalbum on 2011-02-17
Freezes are often a symptom of bad RAM. I'd suggest running Memtest86+ from the GRUB boot menu (run it overnight, if the computer is crashed or there are any errors reported then the RAM is bad) or the memory benchmarks from Phoronix Test suite. The benchmarks will usually crash the computer immediately if there is bad RAM present.

---

