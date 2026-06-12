---
title: "Lucid upgraded some packages and failed to boot afterwards"
date: 2010-10-22
forum: General Help
---

### Post by Fulanicus on 2010-10-22
This problem is proving hard to describe, since the system gave me almost no info and I really don't know how to get more (I'm one of those folks who moved to Ubuntu without being a Linux expert ).

First, I run Ubuntu 10.04 x64 with both Gnome and Xubuntu installed. I use LUKS for full disk encryption, which I installed with the Lucid alternate installer. I have /boot plus all the nested file systems that LUKS creates.

I haven't upgraded to Maverick, nor do I plan to, since I depend so heavily on this machine. But I do update (security, recommended and backports), and for a few key apps I've also installed the lucid-proposed versions.

Anyway, I updated a series of things through the update manager (including, I *believe*, the kernel) and upon reboot I entered my password for LUKS. It was accepted, but after 20-30 seconds the process stopped and gave me the option to drop to a console, ignore or wait. Ignore what, I don't know -- there was no information, really (this was at Xubuntu's screen, which became the default after adding the Xubuntu desktop, but this is originally a Gnome system, and I still use Gnome mostly).

I had no idea what to do at the console, so I tried to proceed anyway, and I ended up with errors about:
- ICE Authority not being able to be updated.
- Problems with the config server (gconf-sanity-check-2 exited with error 256).
- init: ureadahead-other process terminated with stat 4.

I rebooted and tried again, chose the previous kernel (.24 generic) got the same message, chose to continue (again, inspite of what, I don't know), and here I am.

And I'm fairly terrified of rebooting.

How can I find out what the error here is, so I can fix it? Any help would be greatly appreciated.

---

### Post by Fulanicus on 2010-10-22
A bit more info... dmesg says this, among other things:

-Valid eCryptfs headers not found in file header region or xattr region
-Either the lower file is not in a valid eCryptfs format, or the key could not be retrieved. Plaintext passthrough mode is not enabled; returning -EIO

Thing is, I'm writing this from the same system right now, so the encrypted partitions were indeed successfully mounted. What does this mean?

---

### Post by 666f6f on 2010-10-22
[bug #372014]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014") may be relevant. 

I wouldn't suggest encryption, if you're new to GNU/Linux. If it breaks you may not be able to recover your data.

---

### Post by Fulanicus on 2010-10-22
> **666f6f said:**
> [bug #372014]("https://bugs.launchpad.net/ubuntu/+source/ecryptfs-utils/+bug/372014") may be relevant. 

Seems like it may be. Unfortunately, there seems to be no fix for it.


>  I wouldn't suggest encryption, if you're new to GNU/Linux. If it breaks you may not be able to recover your data.

Not new, but not an expert by any means.

---

### Post by 666f6f on 2010-10-22
> **Fulanicus said:**
> Not new, but not an expert by any means.

Me neither!

---

