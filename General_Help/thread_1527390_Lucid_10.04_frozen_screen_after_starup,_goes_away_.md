---
title: "Lucid 10.04: frozen screen after starup, goes away after doing ctrl-alt-f1  [f1-f6]"
date: 2010-07-09
forum: General Help
---

### Post by incubus0h on 2010-07-09
Hi all:

I had upgraded my ubuntu** GNOME desktop** machine (Dell XPS 400) from 9.10 to 10.04 
about a month ago. Things were going fine... till yesterday. Yesterday morning I did a
normal update.

Here is the update log from 'Synaptic > File > History':

---- log start ------
Commit Log for Thu Jul  8 08:43:52 2010


Upgraded the following packages:
acroread (9.3.2-lucid1) to 9.3.3-1lucid1
at-spi (1.30.0-0ubuntu2) to 1.30.1-0ubuntu1
evince (2.30.3-0ubuntu1) to 2.30.3-0ubuntu1.1
gir1.0-atk-1.0 (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
gnome-orca (2.30.0-0ubuntu3) to 2.30.2-0ubuntu1
gnome-panel (1:2.30.2-0ubuntu0.1) to 1:2.30.2-0ubuntu0.2
gnome-panel-data (1:2.30.2-0ubuntu0.1) to 1:2.30.2-0ubuntu0.2
grub-common (1.98-1ubuntu6) to 1.98-1ubuntu7
grub-pc (1.98-1ubuntu6) to 1.98-1ubuntu7
libatk1.0-0 (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libatk1.0-data (1.30.0-0ubuntu2) to 1.30.0-0ubuntu2.1
libatspi1.0-0 (1.30.0-0ubuntu2) to 1.30.1-0ubuntu1
libdbusmenu-glib1 (0.2.9-0ubuntu3) to 0.2.9-0ubuntu3.1
libdbusmenu-gtk1 (0.2.9-0ubuntu3) to 0.2.9-0ubuntu3.1
libevdocument2 (2.30.3-0ubuntu1) to 2.30.3-0ubuntu1.1
libevview2 (2.30.3-0ubuntu1) to 2.30.3-0ubuntu1.1
libnautilus-extension1 (1:2.30.1-0ubuntu1) to 1:2.30.1-0ubuntu1.1
libpam-modules (1.1.1-2ubuntu3) to 1.1.1-2ubuntu5
libpam-runtime (1.1.1-2ubuntu3) to 1.1.1-2ubuntu5
libpam0g (1.1.1-2ubuntu3) to 1.1.1-2ubuntu5
libpanel-applet2-0 (1:2.30.2-0ubuntu0.1) to 1:2.30.2-0ubuntu0.2
linux-generic (2.6.32.23.24) to 2.6.32.24.25
linux-headers-generic (2.6.32.23.24) to 2.6.32.24.25
linux-image-generic (2.6.32.23.24) to 2.6.32.24.25
linux-libc-dev (2.6.32-23.37) to 2.6.32-24.38
nautilus (1:2.30.1-0ubuntu1) to 1:2.30.1-0ubuntu1.1
nautilus-data (1:2.30.1-0ubuntu1) to 1:2.30.1-0ubuntu1.1
python-pyatspi (1.30.0-0ubuntu2) to 1.30.1-0ubuntu1
update-manager (1:0.134.9) to 1:0.134.10
update-manager-core (1:0.134.9) to 1:0.134.10
update-manager-kde (1:0.134.9) to 1:0.134.10

Installed the following packages:
linux-headers-2.6.32-24 (2.6.32-24.38)
linux-headers-2.6.32-24-generic (2.6.32-24.38)
linux-image-2.6.32-24-generic (2.6.32-24.38)

--- log end ----

Since then I have noticed following problems:

1. when I reboot my desktop computer, after the BIOS boot, I get a graphical screen
   with Ubuntu name in the middle with 5 big dots getting filled up one after another 
   ( I guess it's a fancy way of showing the booting sequence ). After that all I get is a
  **'frozen screen'** - basically a screen with purple color background (same as the
  default color theme of the Lucid release) with 14-15 dots near the top and name 
  'Ubuntu' name near the bottom in big letters repeating 5-6 times.
  
   The important thing is that, if I press 'ctrl-alt-f1' (or for that matter, any key from f2
   to f6 instead of f1 will do), and again press 'ctrl-alt-f7', then I see the login prompt
   for users of the machine (normally this is what supposed to happen).

2. After I log in as one user (say User A), and then try to switch to another user (right-
   clicking on the 'turn-off' icon on the top panel and selecting 'Switch from [User A] .. 
   [User B]),  again I get a hung screen. But this time it's all garbage on the screen.
 
   Again I do the 'ctrl-alt-f1' trick, and I get the locked screen for me (User A). I am not
  able to switch to the other user at all, unless I log out and log in as the other user.

Some relevant info:

$ uname -a
Linux [machine name] 2.6.32-24-generic #38-Ubuntu SMP Mon Jul 5 09:22:14 UTC 2010 i686 GNU/Linux

$ lspci -nn | grep VGA
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc RV370 5B60 [Radeon X300 (PCIE)] [1002:5b60]

Thinking that there is problem with the fglrx package, I opted for the second solution
"Problem: Need to fully remove -fglrx and reinstall -ati from scratch" from here: 
[https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver](https://wiki.ubuntu.com/X/Troubleshooting/FglrxInteferesWithRadeonDriver)

But that didn't solve the problem.

So I am wondering if any of you is facing this issue. Any solutions or tricks to fix this
problem is welcome.

Thanks.

---

### Post by ajgreeny on 2010-07-09
Have you tried using the default kernel instead of your 24 version, which must be from either the backports or proposed repository, as the default is 2.6.32-23, not -24.  Maybe the kernel you are using is causing a conflict of some kind.

---

### Post by incubus0h on 2010-07-30
Thanks for your solution. 

But I found the real problem: the Ubuntu 10.04 has new kernel video architecture. As per 
the release notes on the 10.04 ([https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture](https://wiki.ubuntu.com/LucidLynx/ReleaseNotes#Working%20around%20bugs%20in%20the%20new%20kernel%20video%20architecture)),
 "Ubuntu 10.04 LTS enables the new kernel-mode-setting (KMS) technology by default on most common video chipsets." and some chipset drivers don't work properly in certain
situation. 

I tried the workaround mentioned in the release note and those problems on my desktop
are all gone now.

Hope this helps others who are facing similar problems.

---

