---
title: "grub and account problems"
date: 2011-10-09
forum: General Help
---

### Post by Manolicious on 2011-10-09
I am currently having so many issues with my system I just sat and wrote a journal of every problem I encountered.

ubuntu release 10.04
GNOME 2.30.2
GRUB 1.97~beta4

when I reach grub I have ubuntu as a my default boot with Arch and Windows XP.  When I try to boot into Arch grub says "error: no such device".  I can still boot into Windows just fine.

When I boot into Ubuntu with kernel 2.6.32-34-generic, it eventually gets to the gui menu after it passes through a distorted image of my desktop.  The Appearance of the icons has changed from my preferred settings to some default safety Appearance.  After clicking through System/Appearance and waiting a while I get this message, 

"Unable to start the settings manager 'gnome-settings-daemon'. Without the GNOME settings manager running, some preferences may not take effect.  Ts could indicated a problem with DBus, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager."

can't click out by pressing OK, freezes window.  Can't exit window either.
Metacity states it is not responding and offers me to Force Quit.  Clicking 'Wait' freezes that window as well, can't exit out of window or switch to Force Quit.

MetaCity states that Metacity itself is not responding, offers to force quit itself. click wait also freeze that window.

Attempt to logout, also freezes.  Metacity offers to force quit logout.  Clicking wait also freezes it. Metacity offers to force quit itself.  Clicking forcequit also causes it to freeze.  All this time processor is silent.

going to a bash window I reboot and boot into the Ubuntu with kernel 2.6.32-34-generic recovery mode.  It tried to take me to a recovery menu, but I can't access the menu as I get flooded with "[####.######]serial8250: too much work for irq18" messages.  Processor is suspiciously quiet during this.  Stops at [150.818150].  I press enter.  I enter bash, no gui screen.  I reboot from bash again. 

Same thing happens for every other past kereal I still have and their respective recovery modes except for the 2.6.31-14. recovery mode.  Instead I get sent to a disk drive check screen where it appears to freeze as three lines repeating the same message pop up
"init: ureadahead-other main process (3723) terminated with status 4".  I pressed C to cancel disk checks. Makes it to gui menu.  Login, appearance still at default.  Tried to open firefox, no response. Now I can't even click on anything in my panel.  Can still reach file directory through Desktop.  Tried opening a pdf file.  Document view opens but doesn't display pdf file. Can open system monitor now, can't see anything unusual.  Still can't click on any other icon on my panel though.  Can still ctrl al F# to a bash window.

Latter I tried reinstalling grub with a Live CD.  I mounted my rood partition a1 and boot partition a2.

sudo mount /dev/sda1 /mnt
sudo mount /dev/sda2 /mnt/boot/
sudo grub-install --root-directory=/mnt/ /dev/sdc

The output for this states everything installed okay.  But when I run

sudo update-grub

I get "grub-probe: error: cannot find a device for /."

I also try to run

sudo update-grub /mnt/sda1

but I get the same error message.

I would like to update my grub menu with the current OSs I have installed and I'd like to access them.  I'd also like to restore my user account to its functional form.  I'd also like to know why every time I encountered a recovery menu I couldn't access it because of these messages that kept popping up.

---

### Post by dino99 on 2011-10-09
if you have so many issues, maybe its time to replace it with a fresh clean installation (~ 30 mn)

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

or clean/autoclean/autoremove the system, deactivate all third party repos if any, then update and reboot in recovery mode -> and select repair package

---

### Post by oldfred on 2011-10-09
You installed grub2's boot loader to sdc?

You can only do the update-grub from inside your install after you have rebooted into it or chrooted into it.

Did you attempt to share /home or /boot between systems. That can lead to the type of errors you are getting. If so dino99's suggest may be the best.

---

