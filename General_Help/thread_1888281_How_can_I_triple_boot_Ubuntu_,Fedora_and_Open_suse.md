---
title: "How can I triple boot Ubuntu ,Fedora and Open suse"
date: 2011-11-28
forum: General Help
---

### Post by asifnaz on 2011-11-28
Hi I am an in-experienced user I am planning to triple boot 

Ubuntu 11.10 (with unity ) Fedora 16 (gnome 3 ) and open suse (KDE)

I have a spare Hard disk so no risk of data lose .

1)any suggestions how should I do that ..?

2)do I need to install grub 3 times ..?

3)do I have to install them in any particular order..?

4)can they share a single swap partition?

thank you

---

### Post by oldfred on 2011-11-29
Whichever system you think may be the one you use the most should be the last install as then that copy of grub will be in control. But Ubuntu's os-prober is very good at finding other systems and adding those to its menu, so I would install Ubuntu last.

You should just be able to create three 20GB partitions for / and one for swap. With one swap you will not be able to hibernate, but Linux boots fast enough that hibernation does not save much if anything.

OpenSuse grub2 from Ubuntu:
[http://ubuntuforums.org/showthread.php?t=1740690](http://ubuntuforums.org/showthread.php?t=1740690)

I have not installed Fedora, but some have commented to not let it use LVM. It normally installs to two partitions a /boot outside the LVM and it puts the main install inside the LVM. But I understand you can specify not to use the LVM during install.

These were older where Fedora used grub legacy. Fedora 16 has now changed to grub2.
HowTo: add Fedora 15 to Maverick Grub 2
[http://ubuntuforums.org/showthread.php?t=1714170](http://ubuntuforums.org/showthread.php?t=1714170)
 [SOLVED] Grub 2 Fedora Install not seen by 40_custom 
[http://ubuntuforums.org/showthread.php?t=1343779](http://ubuntuforums.org/showthread.php?t=1343779)

---

### Post by oldfred on 2011-11-29
See also this thread, with same issues. It looks liek OpenSuse also wants a separate /boot. Do not attempt to share /boot.

[http://ubuntuforums.org/showthread.php?t=1885181](http://ubuntuforums.org/showthread.php?t=1885181)

---

### Post by asifnaz on 2011-11-30
> **oldfred said:**
> See also this thread, with same issues. It looks liek OpenSuse also wants a separate /boot. Do not attempt to share /boot.

[http://ubuntuforums.org/showthread.php?t=1885181](http://ubuntuforums.org/showthread.php?t=1885181)


Thank you so much for detailed answer

---

