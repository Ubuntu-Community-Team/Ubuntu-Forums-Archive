---
title: "Ubuntu 9.10 - Display periodically freezes"
date: 2010-01-02
forum: General Help
---

### Post by shayzu on 2010-01-02
Hi

My name is Shay and I am a new "convert" to Ubuntu.
I have been using Fedora (from 7 up to 12) as my desktop, and decided to switch to Ubuntu mainly because of frequent freezes of the desktop after the last upgrade to Fedora 12.

From past experience. I understood that the cause of the freezes would be KMS issues, and for Fedora 11, the problem was solved by adding "nomodeset" to the kernel parameter in Grub's menu.
Since this change did not solve the issue for Fedora 12, I'd decided to move to Ubuntu.
What can I say - it's far superior  to Fedora in any respect - except for the fact that the display keeps freezing too!!!

I've tried any option I could find:
1. In 9.10 release notes, there's an issue: "No Xv support for Intel 82852/855GM video chips with KMS" [http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS]("http://www.ubuntu.com/getubuntu/releasenotes/910#No%20Xv%20support%20for%20Intel%2082852/855GM%20video%20chips%20with%20KMS")
I'd followed the instructions how to disable KMS - and rebooted my desktop.
This did not affect anything.
2. Next, the parameter: i915.modeset=0 was added. This time results were BAD: boot process had frozed, so using Grub's online editor both parameters were removed and the OS has managed to start.
3. Tried to mess around Compiz's parameters - but could not find any helpful one.

Bottom line - I am in dead end; I would like to continue using Ubuntu, but the periodical freezes are a&#1502; annoyance, which only the quick boot covers it up.

I have seen lot of complaints about KMS and Intel graphic chips - where KMS disabling had solved their problems - but not for me.

As far as I can see - it looks like that I don't correctly disable KMS - or there's another issue.
Could anyone provide me a lead how to handle the issue?

Some information about my machine:

uname -a
Linux shay 2.6.31-16-generic #53-Ubuntu SMP Tue Dec 8 04:01:29 UTC 2009 i686 GNU/Linux
lspci -nn | grep -i vga
00:02.0 VGA compatible controller [0300]: Intel Corporation 82G33/G31 Express Integrated Graphics Controller [8086:29c2] (rev 02)

Thanks!!

Shay

---

