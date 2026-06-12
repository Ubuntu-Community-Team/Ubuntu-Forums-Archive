---
title: "Ubuntu 11.04 hangs on start-up"
date: 2011-07-30
forum: General Help
---

### Post by billbodewig on 2011-07-30
Hi starting again with Linux since I crashed W7 and got tired of it.

Running Ubuntu 1104 on Toshiba G30 with two drives.

Installed 1104 on SDA

Two problems

1. On computer start-up it freezes, blank display with no action from the HDD

2. On selecting the HDD from the menu by pressing F12 and then HDD1
I get the same problem.

I can overcome this by changing grub to 'noquiet nosplash nomodeset'

but then I get of course the full goomph on the screen.

Anyone have a solution?

Could this be a display driver problem since I noticed that I can not get the full 1920 x 1200 resolution?

Appreciate it guys and dolls.

---

### Post by billbodewig on 2011-07-31
OK here is what happens

Machine a Qosmio G30 with two internal HDD. W7 crashed and decided to install Linux Mint 11 on sda.

SDA was formatted using gparted to ext4.

Tried the live CD and it worked fine except for the "low" resolution of 1280 instead of 1920 pixels. Probably due to drivers on the distro.

Installed Mint on the computer. Did not start automatically so went to Toshiba start-up and selected HDD1. Same problem. Adjusted bootup by including 'noquiet nosplash nomodeset'. Could start and use the system but display still lousy.

Removed Linux Mint and installed Ubuntu natty immediately; no trial. Same problem with the start up and the display. Tried the live CD, display now 1920 x 1200. Re-installed Ubuntu now getting the hi-res display as on the lve CD but still no direct start during boot up.

Tried to install Linux Mint on sdb. Went into gparted from the Mint live CD but could not format sdb. gparted when asked to format sdb went straight to sda. 

Installed nevertheless and during installation tells me of the Ubuntu installed s/w and asked what to do. Left Ubuntu on sda, expecting Linux Mint to form a partition and install on the same drive. Instead it installed on sdb AND starts directly on boot up.

Someone who knows the insides of the Ubuntu kernel please tell me what is going on.

---

### Post by varunendra on 2011-07-31
> **billbodewig said:**
> OK here is what happens

Machine a Qosmio G30 with two internal HDD. W7 crashed and decided to install Linux Mint 11 on sda.

SDA was formatted using gparted to ext4.

Tried the live CD and it worked fine except for the "low" resolution of 1280 instead of 1920 pixels. Probably due to drivers on the distro.

Installed Mint on the computer. Did not start automatically so went to Toshiba start-up and selected HDD1. Same problem. Adjusted bootup by including 'noquiet nosplash nomodeset'. Could start and use the system but display still lousy.

Removed Linux Mint and installed Ubuntu natty immediately; no trial. Same problem with the start up and the display. Tried the live CD, display now 1920 x 1200. Re-installed Ubuntu now getting the hi-res display as on the lve CD but still no direct start during boot up.

Tried to install Linux Mint on sdb. Went into gparted from the Mint live CD but could not format sdb. gparted when asked to format sdb went straight to sda. 

Installed nevertheless and during installation tells me of the Ubuntu installed s/w and asked what to do. Left Ubuntu on sda, expecting Linux Mint to form a partition and install on the same drive. Instead it installed on sdb AND starts directly on boot up.

Someone who knows the insides of the Ubuntu kernel please tell me what is going on.
Hi,
Although a few things are not clear by your description, the most probable explanation for the booting issue is that perhaps the BIOS is set to boot from the hard drive that appears as 'sdb' in ubuntu.

If you want an accurate info about 'what is where', download '[boot info script]("http://bootinfoscript.sourceforge.net/")' and run it as described in the linked page. Then post the output 'RESULT.txt' file's contents here.

If mint boots correctly now but does not you the give option to boot ubuntu, open terminal and run:
```
sudo update-grub
```

---

### Post by billbodewig on 2011-09-25
Problem seemed to have solved itself and most likely was due to incorrect actions during shut-down (?) since it very occasionally re-appears; like this morning.

Inserted the DVD with the ISO, booted from there, shut-down, booted normally; no problem.):P

---

