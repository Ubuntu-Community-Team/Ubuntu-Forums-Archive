---
title: "Grub2 will not boot ubuntu, and stays at terminal"
date: 2010-08-06
forum: General Help
---

### Post by kuraykillua on 2010-08-06
So I've installed Ubuntu on a laptop, using the alternate CD I installed an encrypted copy. After installing the NVidia drivers, the plymouth splash screen's resolution (login splash) got screwed up, and I tried to fix it (expected). The splash screen is also the screen where I enter the encryption code for my encrypted Ubuntu. After manually changing the grub's boot resolution didn't work (text edit grub, and then update-grub), I tried startup manager to change resolution. That didn't work either. In fact Neither of them work. Changing ANY settings in startup manager or text grub with update takes no effect, even though the resolution I chose was supposedly supported by that weird bios video thing.
So, I tried to reinstall Grub2.
I followed the following instructions:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
Now when I start my computer, it goes into GNU GRUB v 1.98, with the following lines
"Minimal BASH-like line editing is supported. For the first word, TAB lists of possible command completions. Anywhere else TAB lists possible device or file completions.
GRUB> _"
And stays there. No menu, nothing.
I assume that due to me installing the encrypted copy, the boot partition is separate.
When I run
Sudo fdisk -l
There's 2 that says Linux, and 1 that's ext. One of the linux ones is significantly smaller than the other.
SO I guessed that I installed grub2 in the wrong partition? However I cannot mount the linux partition that's bigger. It asks for my encryption password, but then says ERROR: Unmountable partition. I'm sure I typed the password correctly, because if I type it wrong, it gives me a different prompt and asks for the password again.
I'm not sure how to get grub2 to attempt to load the encrypted partition either...
What do I do? Grub is annoyingly frustrating to get to work correctly.

(The exact error message is: Unable to mount 120 GB LVM2 Physical Volume)
(Not a mountable file system)
If I type
Sudo mount /dev/sda5 /media/sda5 (which is my encrypted partition) it says
Mount: unknown filesystem type 'crypto_LUKS'

---

### Post by rtimai on 2010-08-23
I checked around and what you describe, "Minimal BASH-like line editing is supported..." you are booting directly into the command line interface (CLI.) Here's information on the commands available in CLI mode.

[http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html](http://members.iinet.net/~herman546/p20/GRUB2%20CLI%20Mode%20Commands.html)

This is over my head to offer any more suggestions. Hopefully someone can tell you what commands to try. GRUB2 is tricky, because it is transitioning its configuration data storage to a different method. It sounds like part of the GRUB2 installation process "chains" the data from one set of files to another, or something like that.

---

