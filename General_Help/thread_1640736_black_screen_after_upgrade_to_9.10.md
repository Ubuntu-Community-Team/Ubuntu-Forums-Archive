---
title: "black screen after upgrade to 9.10"
date: 2010-12-08
forum: General Help
---

### Post by bernardfrancois on 2010-12-08
A few days ago I upgraded my ubuntu to 9.10.

After booting, I now get a black screen. So I don't see a login screen or a graphical loading screen.
I don't have a clue what's wrong, as I don't see any error messages.

I tried the following things to find out what's the problem:
[LIST]
[*] I checked /var/log/Xorg.0.log, and noticed there are no errors in this log file.
[*] I tried connecting my screen to the other connector on my graphics card and rebooted, but the issue remained.
[*]  I modified /boot/grub/menu.lst to make sure the latest installed kernel is used (found the latest installed kernel by running 'dpkg -- list | grep linux-image'). This didn't help, but I left it like this as it's probably better to use the kernel that came with the upgrade.
[*] I added a line 'acpi=off noapic nolapic' to /boot/grub/menu.lst as suggested here ([http://ubuntuforums.org/showthread.php?t=1634285&highlight=black+screen+upgrade+9.10](http://ubuntuforums.org/showthread.php?t=1634285&highlight=black+screen+upgrade+9.10)). This had no effect, so I removed the line again.
[*] I disabled xorg.conf (using 'sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup') as suggested here ([http://ubuntuforums.org/showthread.php?t=1356138](http://ubuntuforums.org/showthread.php?t=1356138)), but reverted this as it also didn't change anything.
[*] I added 'nomodeset' after the kernel line of the boot entry I'm using (as suggested in [http://ubuntuforums.org/showthread.php?t=1614269&highlight=black+screen+upgrade+9.10](http://ubuntuforums.org/showthread.php?t=1614269&highlight=black+screen+upgrade+9.10) ). This didn't change anything, so I reverted the change again.
[*] I had a quick look at the output of the 'dmesg' command but didn't notice anything looking like an error. I may have overlooked it though or not recognised it as an error.
[/LIST]

Is there anyone who could help me to find out what's causing this? Without knowing what could be the cause, it's quite hard to come up with a solution...

---

### Post by Rubi1200 on 2010-12-08
Hi,
what graphics card do you have installed and how much RAM?

what version did you upgrade from?

Please boot the computer with a LiveCD and run the boot info script linked at the bottom of my post.

Once completed, post the results back here.

Thanks.

---

