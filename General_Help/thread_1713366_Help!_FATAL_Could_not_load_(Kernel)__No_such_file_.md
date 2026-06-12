---
title: "Help! FATAL: Could not load (Kernel) : No such file or directory"
date: 2011-03-24
forum: General Help
---

### Post by Dakobah on 2011-03-24
I should preface this by saying that I'm a completely new user.

I installed Ubuntu because I was sick of using Windows. Turns out I really like Ubuntu. I thought I had gotten(kind of) the hang of it, I was gaming and fixing my own problems before long..everything was going good until I bought a new video card (ATI Radeon HD 6950). Once I swapped out my old Geforce GTS 250 for my new ATI and booted up all I could get to was a login screen. I tried "startx" but it just said (EE) No screens found and then an error about the nvidia module not being found. So, I put my geofce back in and it worked fine. I searched the forums for solutions and found some having to do with installing linux-headers.. Well, my first mistake was messing with the headers.  Then I got locked out of my system, both cards wouldn't work. Fortunately after a ton of messing around I've finally got to boot into Failsafe graphics mode, as its the only one that works.(Also in the grub boot list, there are three different kernels with 3 separate recovery versions). Anyhow, I thought I should maybe install the ATI drivers and this is the error I get:


justin@Gabe:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
justin@Gabe:~$ sudo apt-get upgrade grub
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
justin@Gabe:~$ sudo get grub
sudo: get: command not found
justin@Gabe:~$ cd catalyst11.2
justin@Gabe:~/catalyst11.2$ sudo dpkg -i fglrx*.deb(Reading database ... 207474 files and directories currently installed.)
Preparing to replace fglrx 2:8.821-0ubuntu1 (using fglrx_8.821-0ubuntu1_amd64.deb) ...
Removing all DKMS Modules
Done.
Unpacking replacement fglrx ...
Preparing to replace fglrx-amdcccle 2:8.821-0ubuntu1 (using fglrx-amdcccle_8.821-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-amdcccle ...
Preparing to replace fglrx-dev 2:8.821-0ubuntu1 (using fglrx-dev_8.821-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-dev ...
Preparing to replace fglrx-modaliases 2:8.821-0ubuntu1 (using fglrx-modaliases_8.821-0ubuntu1_amd64.deb) ...
Unpacking replacement fglrx-modaliases ...
Setting up fglrx (2:8.821-0ubuntu1) ...
update-initramfs: deferring update (trigger activated)
Loading new fglrx-8.821 DKMS files...
Building only for 2.6.35-28-generic
Building for architecture x86_64
Building initial module for 2.6.35-28-generic
Done.

fglrx.ko:
Running module version sanity check.
 - Original module
   - No original module exists within this kernel
 - Installation
   - Installing to /lib/modules/2.6.35-28-generic/updates/dkms/

depmod......

DKMS: install Completed.
update-initramfs: deferring update (trigger activated)
Setting up fglrx-modaliases (2:8.821-0ubuntu1) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Processing triggers for python-gmenu ...
Rebuilding /usr/share/applications/desktop.en_US.utf8.cache...
Setting up fglrx-amdcccle (2:8.821-0ubuntu1) ...
Setting up fglrx-dev (2:8.821-0ubuntu1) ...
Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.38-020638rc8-generic
grep: /boot/config-2.6.38-020638rc8-generic: No such file or directory
WARNING: missing /lib/modules/2.6.38-020638rc8-generic
Device driver support needs thus be built-in linux image!
WARNING: Couldn't open directory /lib/modules/2.6.38-020638rc8-generic: No such file or directory
FATAL: Could not open /lib/modules/2.6.38-020638rc8-generic/modules.dep.temp for writing: No such file or directory
FATAL: Could not load /lib/modules/2.6.38-020638rc8-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.38-020638rc8-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.38-020638rc8-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.38-020638rc8-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.38-020638rc8-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.38-020638rc8-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.38-020638rc8-generic/modules.dep: No such file or directory
FATAL: Could not load /lib/modules/2.6.38-020638rc8-generic/modules.dep: No such file or directory



The 2.6.38-020638rc8 kernel doesn't existed anymore, I removed it, but its still only pointing to that kernel, I've tried reinstalling different versions of kernels, but it wont stop pointing to the non-existent one.



Any ideas guys? And be gentle, I'm a newbie.

---

### Post by bishnusushila on 2011-03-24
[INDENT][FONT=arial][SIZE=2][COLOR=#ff0000][B]Dear all,
in my web show the following error message how to solve it.

SQL/DB Error --[/B] [[/COLOR][/SIZE][/FONT]
[LIST=1][FONT=arial][SIZE=2][COLOR=#ff0000][COLOR=#000077]**Error establishing a database connection!**
[*]Are you sure you have the correct user/password?
[*]Are you sure that you have typed the correct hostname?
[*]Are you sure that the database server is running?[/COLOR][/COLOR][/SIZE][/FONT]
[/LIST]
[FONT=arial][SIZE=2][COLOR=#ff0000]][/COLOR][/SIZE][/FONT][/INDENT][INDENT][FONT=arial][SIZE=2][COLOR=#ff0000]**SQL/DB Error --** [[/COLOR][/SIZE][/FONT]
[LIST=1][FONT=arial][SIZE=2][COLOR=#ff0000][COLOR=#000077]**Error selecting database _dbahs_!**
[*]Are you sure it exists?
[*]Are you sure there is a valid database connection?[/COLOR][/COLOR][/SIZE][/FONT]
[/LIST]
[FONT=arial][SIZE=2][COLOR=#ff0000]][/COLOR][/SIZE][/FONT][/INDENT]

---

### Post by Dakobah on 2011-03-24
bump*

---

### Post by Dakobah on 2011-03-24
Figured it out.

---

### Post by Another Monkey on 2011-03-24
Figured it out?  Great!
Post the details and then mark the thread as "Solved" to help others.

---

