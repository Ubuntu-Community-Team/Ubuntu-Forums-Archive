---
title: "Boot hangs after updating?"
date: 2011-03-10
forum: General Help
---

### Post by pseudosmart on 2011-03-10
So I tried installing the nvidia drivers for my GeForce 330M using Jockey after I first installed 10.10, but it did not make it so my desktop was not bigger than my screen. So, I blacklisted nouveau by creating a text file which had in it:

blacklist nouveau
options nouveau modeset=0

Then I saved the file as disable-nouveau.conf, then chown(ed) it to be owned by root, and moved it to /etc/modprobe.d/

I then installed the driver for my nvidia card, and everything worked perfectly. But after installing the updates listed in the update manager, my computer won't even boot to the GUI desktop, it just hangs. I can still access the command line, but when press <ctrl-alt-F7>, all I see is this:


fsck from util-linux-ng 2.17.2
//dev/sda1: clean 170760/29409280 files, 5091535/117623296 blocks
   *Starting AppArmor profiles
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox

   *Setting sensors limits
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
   *Starting the Windbind daemon winbind


And that's it. It just hangs there. Like I said, I can still access the command line with <ctrl-alt-F1>, but I have no idea how to get Gnome I guess to display? I'm very new at this, and would really appreciate any help that anyone has to offer. Thanks in advance.

---

### Post by pseudosmart on 2011-03-10
Ok, wow, that was fast. In playing around in the command line, I just reinstalled the nvidia driver that I had saved in my Desktop directory. But nothing happened when I typed sudo /etc/init.d/gdm start? And the boot screen was still hanging when I pressed <ctrl-atl-F7>? But apparently, after I rebooted, the system booted fine, right to my desktop, and it looks like all my updates were installed with no problems. Sorry for wasting anybody's time with this.

---

