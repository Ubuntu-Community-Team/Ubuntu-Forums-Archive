---
title: "ATI Catalyst uninstall script trashed my system - HELP!"
date: 2011-04-03
forum: General Help
---

### Post by Zorgoth on 2011-04-03
I run Ubuntu 10.04 Lucid with an ATI Mobility Radeon 5470.  I heard that a bug I was having using Catalyst 11.2 might not happen in Catalyst 10.10, so I ran sudo /usr/share/ati/fglrx-uninstall.sh and then installed Catalyst 10.10.  I have installed many catalyst drivers as I have to do it whenever I get a new kernel, and it always works fine.

Except it didn't install.  No matter how many times I restarted my computer and uninstalled/reinstalled my drivers, it came up with metacity and no OpenGL support.  I tried both 10.10 and 11.2 repeatedly.  Worse still, my computer no longer shuts down properly.  If I try to do it from the desktop, my computer hangs forever, and if I type sudo shutdown now in a terminal, it shuts down instantaneously and reboots, and then does disk check on reboot.  Also, only tty7 with the desktop works properly.  If I use Ctrl-Alt-F1 through Ctrl-Alt-F6, I get a black screen until I Ctrl-Alt-F7 back to the desktop.

Then I decided that to fix it I would try reinstalling the kernel.

First using remove and then completely remove I reinstalled all the packages relating to kernel version 2.6.32-30.

remove did nothing and completely remove broke it; now I get a kernel panic about mounting the root fs every time I try to boot with that kernel.

I can boot into kernel version 2.6.32-28, but it has the same graphics problems, the same shutdown problem, and the same problem with ttys as 2.6.32-30 did.

Does anyone have any possible solution to this problem other than reinstalling my OS (which I plan to try shortly)?

---

### Post by sandyd on 2011-04-03
> **Zorgoth said:**
> I run Ubuntu 10.04 Lucid with an ATI Mobility Radeon 5470.  I heard that a bug I was having using Catalyst 11.2 might not happen in Catalyst 10.10, so I ran sudo /usr/share/ati/fglrx-uninstall.sh and then installed Catalyst 10.10.  I have installed many catalyst drivers as I have to do it whenever I get a new kernel, and it always works fine.

Except it didn't install.  No matter how many times I restarted my computer and uninstalled/reinstalled my drivers, it came up with metacity and no OpenGL support.  I tried both 10.10 and 11.2 repeatedly.  Worse still, my computer no longer shuts down properly.  If I try to do it from the desktop, my computer hangs forever, and if I type sudo shutdown now in a terminal, it shuts down instantaneously and reboots, and then does disk check on reboot.  Also, only tty7 with the desktop works properly.  If I use Ctrl-Alt-F1 through Ctrl-Alt-F6, I get a black screen until I Ctrl-Alt-F7 back to the desktop.

Then I decided that to fix it I would try reinstalling the kernel.

First using remove and then completely remove I reinstalled all the packages relating to kernel version 2.6.32-30.

remove did nothing and completely remove broke it; now I get a kernel panic about mounting the root fs every time I try to boot with that kernel.

I can boot into kernel version 2.6.32-28, but it has the same graphics problems, the same shutdown problem, and the same problem with ttys as 2.6.32-30 did.

Does anyone have any possible solution to this problem other than reinstalling my OS (which I plan to try shortly)?
First, remove fglrx, and convert back to the normal drivers.
If fglrx somehow hates you, and doesn't uninstall the kernel modules, you can delete them in /lib/modules (I don' remember which folder they are in), or black list them.

Now, follow the instructions here to remove fglrx [https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver#Problem:%20%20Need%20to%20fully%20remove%20-fglrx%20and%20reinstall%20-ati%20from%20scratch) .

Since your having issues, I might advise that you try the xorg-edgers ppa, since gallium infrastructure exists for your card. Gallium offers much improved graphics performance compared to the classic (what you get when you install ubuntu) drivers.

---

