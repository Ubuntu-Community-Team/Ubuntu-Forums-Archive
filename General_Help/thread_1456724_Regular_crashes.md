---
title: "Regular crashes"
date: 2010-04-17
forum: General Help
---

### Post by dapissarenko on 2010-04-17
Hello!

I installed xubuntu 9.10 a couple of days ago. I also installed security and recommended updates.

I experience following problem: The computer regularly shuts down. I can't figure out, why it happens.

Originally, I thought that this was caused by a synchronization process of Evolution and Palm.

However, a couple of minutes ago the computer crashed again, while I was surfing the Internet (watching a video, to be precise).

Question: How can I figure out what causes this behavor?

Notes:

1) The machine is an old laptop with Intel Celeron processor (1 GHz, 500 MB RAM, 40 GB disk).

2) I could not boot the machine after the installation (neither in normal, nor in recovery mode) until I added the "acpi=off" parameter to the GRUB configuration.

3) I installed some packages, which were necessary for playing MP3 files, including "ugly" and "bad" ones.

Thanks in advance

Dmitri

---

### Post by dapissarenko on 2010-04-18
Hello!

I also noticed that before shutdown the CPU load is always 100 %.

Is it thinkable that the computer shuts down because the CPU becomes too hot due to high load?

Is it possible that it happens because ACPI is turned off?

Note: I think it is a software issue, not hardware problem because previously I ran *Windows XP Home* and an old *Ubuntu* on the same machine and never experienced such problems.

Thanks in advance

Dmitri

P. S.: Output of commands *dmesg* as well as the contents of files */var/log/messages* and */var/log/syslog* can be found in attachment.

---

