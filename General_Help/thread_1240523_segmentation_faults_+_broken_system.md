---
title: "segmentation faults + broken system"
date: 2009-08-14
forum: General Help
---

### Post by eyescrm on 2009-08-14
I've been experiencing some anomalies over the past few weeks as you can read here [http://ubuntuforums.org/showthread.php?t=1229622](http://ubuntuforums.org/showthread.php?t=1229622)

Last night my game (Heroes of Newerth, awesome game, plus it has a Linux client!) crashed when, at the same time, the power management icon showed up in my panel. The icon is never there, I have not enabled it, I am not on a laptop or anything.
Then my desktop was unresponsive and I could not select anything.
I rebooted.

After the reboot I started having segmentation faults all over the place. Firefox. conky. Banshee. You name it.
I started googling but I could not find anything helpful, so I decided to simply format and reinstall Ubuntu. I also formatted my home folder in the process. (I left my music and some other data on my second HDD, in case that is important at all.)

After formatting everything seemed fine. I downloaded all the updates and then I installed Firefox 3.5 which started once but then returned a segmentation fault whenever I tried to start it again. (Though, this could be related to the Ubuntu start menu, I did not check at the time.)
I installed conky (the repository version) which started fine the first time. The second time it returned a segmentation fault. Other apps seemed to do the same.

I rebooted several times with different outcomes.
Somtimes it would freeze during the booting procedure, sometimes it would go to the login screen where I could log in.
Either it would log me in fine or I would end up at a black screen before the desktop fully loaded. There I could either do nothing but a hard reboot or enter a terminal and try to reboot/halt. Sudo halt would mostly result in a black screen with just my cursor showing, yet it would be frozen. Sudo reboot would usually return lots of segfault errors.

When I tried a LiveCD and clicked on either Try Ubuntu without changing your system or Install Ubuntu lots of numbers appeared that ended with ---[ end trace <some number> ]--- and then either nothing or "Fixing recursive fault but reboot is needed!" a line after that.

Formatting did not seem to work, even after several attempts.

I have tried fsck and memtest, both were fine.
I am/was running Ubuntu 9.04 x86_64.

I am out of ideas and I am guessing it must be hardware-related.

Any help really appreciated.

---

### Post by eyescrm on 2009-08-15
Formatting now worked and everything seemed fine again at first.
I did not install any updates like last time.
I installed conky first and started it multiple times and tried rebooting and repeating that, no problems there.
Then I did what I had done last time. I installed Firefox 3.5, Started and closed it several times without problems. Then I installed 3 popular addons, restarted the browser and it returned "Segmentation Fault" again.

I ran memtest and fsck again just to be safe. No errors occurred.

---

### Post by eyescrm on 2009-08-22
After my last post I formatted again.
Everything seemed normal but once while playing a game, compiz stopped working, my gnome-panel was gone and I could not launch anything from my dock (cairo-dock) either.
After a reboot everything was normal again and that's the only time it ever occured.

A few days later I had a freeze shortly after booting again. Rebooting was fine, though. No segmentation faults or anything.

Now, another few days later while watching a video in vlc my system froze with the sound continuously repeating. That has never happened before. I logged into a TTY terminal and tried sudo reboot.
It said: program usplash[169]: segfault at ffffffcc ip 00007f8be5e31375 sp 00007fffeea4bfc0 error 6 in libx86.so.1[7f8be5e16000+20000].

I hard-rebooted and received yet another error: Kernel Panic - not syncing: Attempted to kill init

After another reboot it returned a different error message with some references to ACPI. Google found a few results regarding ACPI issues but nothing seemed to fit my problem, again.

Some lines from var/log/messages that struck me as weird:

[40170.894028] python[26956] general protection ip:7f2ee16a8a06 sp:7fffe98b68b0 error:0 in ld-2.9.so[7f2ee169d000+20000]
[40170.937017] python[26959] general protection ip:7f0aa5e33a06 sp:7fffae03f040 error:0 in ld-2.9.so[7f0aa5e28000+20000]
[40251.191285] hald[7879] general protection ip:40e57c sp:7fff7865f2a0 error:0 in hald[400000+57000]
[40401.670247] gnome-power-man[8755] general protection ip:7fbcecda49a9 sp:7ffff7f0aa00 error:0 in libdbus-1.so.3.4.0[7fbcecd7b000+3c000]
[40980.344382] gnome-power-man[28425]: segfault at 7fd74b5c2654 ip 00007fd74a89108b sp 00007fff52aa4440 error 4 in ld-2.9.so[7fd74a887000+20000]

vlc[15814] general protection ip:7ffa7c7026a2 sp:7ffa7949f968 error:0 in libc-2.9.so[7ffa7c682000+168000] this one happened a few minutes ago when vlc crashed. (A different crash, not the one that froze my system. In this case just vlc crashed.)

When I tried booting again after the two failed times it booted normally and I am using the pc as usual right now, everything _seems_ normal.

Any indication as to what may cause this, or whether it is more likely hardware than software-related (or vice versa), would already be very helpful.

---

### Post by eyescrm on 2009-08-24
I figured I would try to install a different distribution as well as a different desktop environment and see whether things like that happen there too.

So I went ahead and installed Arch Linux and KDE and within a day of installation I experienced problems.

Konsole wouldn't start anymore at some point, yet everything else seemed normal. I changed to a virtual terminal (without doing anything) and back and it froze.

After a hard reboot I found this in the logs:
konsole[4204] general protection ip:7fda6e8adca6 sp: 7fff5d0f95d8 error:0 in libkdecore.so.5.3.0[7fda6e7ae000+275000]

About an hour after that Firefox, Dolphin and most other apps were suddenly unresponsive. I tried to reboot (logout -> restart) and I ended up in a virtual terminal. I tried to start X again but that returned errors. Neither halt nor reboot would work either. (The message "Going down for reboot/halt" appeared though.)

One hard reboot later I found myself with this error:
Kernel panic - not syncing: Out of memory and no killable processes

After another hard reboot it went straight to KDM login window and everything worked normally again.
I rebooted to see what would happen. It rebooted and I landed in a virtual terminal. I logged in as root and it said "Last Login: [...]" before disappearing a second later, returning me to the login prompt. So logging in was not possible, not with my normal user account either.

I rebooted and it showed lots of this:
/sbin/agetty: symbol lookup error: /lib/libc.so.6: undefined symbol: _nl_msg_cat_cjtr, version GLIBC_2.2.5

followed by:
INIT: Id "c1" (there were 4 more entries, c2 through c5) respawn too fast: disabled for 5 minutes
INIT: no more processes left in this runlevel

I tried again and I ended up in the KDM login screen again, with everything seeming normal

I rebooted again and went through the BIOS options again. I left the BIOS and during the booting procedure it stopped at "Filesystem Check [FAIL]" "reboot required, automatically rebooting in 15 seconds"

After a reboot I got to the KDM login menu again and was able to log in normally again. It seems to be running as usual.

Also, my hardware:

XFX 512 GTS 250
Intel Q9550 775 2833 BOX1333 12M
Corsair CMPSU-520HX 520W ATX2
Creative X-Fi Titanium PCIe (which I'm not using, though)
Asus P5Q-Pro P45
Kingston 4GB 1066-555 Dual Channel
Western Digital 320 GB SAT2 WD3200AAKS (two of those)
Lite-On DH-16D2S DVD drive

---

