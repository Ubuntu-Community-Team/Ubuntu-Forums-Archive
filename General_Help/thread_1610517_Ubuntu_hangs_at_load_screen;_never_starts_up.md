---
title: "Ubuntu hangs at load screen; never starts up"
date: 2010-10-31
forum: General Help
---

### Post by Andante on 2010-10-31
Hi everyone,

I recently posted here and with help retrieved my files from my Ubuntu partition, so that's one issue solved.

Now I'm trying to run Ubuntu again. The problem started when I put Ubuntu to sleep, but instead it turned the screen black and hung without going into sleep (this is common for me). I had to cut its power, but afterwards it wouldn't boot.

I tried booting off old kernel and "recovery" ones, but that gives me an error and loads "ash" shell, which doesn't let me browse any of my files (no /home director to speak of).

I'm really at a loss. Is my only option to delete everything and reinstall? If I back-up my home directory, can I just copy/paste the contents into it once I install a new Ubuntu and have things more or less in working order?

(Perhaps more importantly, is there any way to improve sleep so this doesn't happen again?)

Thanks for your help!

---

### Post by bibble235 on 2010-11-01
I would put the original boot disk in and boot off that.

Do an fsck on the disk and mount it to check it works.

Regards,
Iain

---

