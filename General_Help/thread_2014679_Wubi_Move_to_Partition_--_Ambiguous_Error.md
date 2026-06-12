---
title: "Wubi Move to Partition -- Ambiguous Error"
date: 2012-07-02
forum: General Help
---

### Post by Racer Of All on 2012-07-02
Hello!

I recently decided to get into the world of linux (still a beginner so bear with me, although I am willing to learn). I originally installed Ubuntu using Wubi but have decided to switch over to a more permanent installation (ew NTFS) anyway shrinking/formatting the partitions went great (done it before).

Now I am trying to follow the instructions found [here]("https://help.ubuntu.com/community/MigrateWubi") on the Wiki but I encounter an error. Here is the terminal log:

```
sudo bash wubi-move-2.2.sh /dev/sda2
wubi-move-2.2.sh:  Validating migration source...
wubi-move-2.2.sh:  Source for migration validated successfully:
wubi-move-2.2.sh:    Wubi host partition: /dev/sda1
wubi-move-2.2.sh:    Size of install: 3774443 K
wubi-move-2.2.sh:    Size of /boot: 48323 K
wubi-move-2.2.sh:    Size of /usr: 1975996 K
wubi-move-2.2.sh:    Size of /home: 388377 K
wubi-move-2.2.sh:  Validating migration target(s)...
wubi-move-2.2.sh:  Target(s) for migration validated successfully:
wubi-move-2.2.sh:    Size of / partition: 25526176 K
wubi-move-2.2.sh:  Target partition size is sufficient

wubi-move-2.2.sh:  Grub2 will be installed to /dev/sda

wubi-move-2.2.sh:  Please close all open files before continuing.
wubi-move-2.2.sh:  About to format the target partition (/dev/sda2).
wubi-move-2.2.sh:  Proceed with format (Y/N)
y
wubi-move-2.2.sh:  Formatting /dev/sda2 with ext4 file system

wubi-move-2.2.sh:  Copying files - please be patient - this takes some time
wubi-move-2.2.sh:  Copying from / (root)
wubi-move-2.2.sh:  Copying from /usr
wubi-move-2.2.sh:  Copying from /boot
wubi-move-2.2.sh:  Copying from /home
wubi-move-2.2.sh:  Copying completed

wubi-move-2.2.sh:  Starting chroot to the target install.
wubi-move-2.2.sh:  Removing lupin-support on target...
[COLOR="Red"]wubi-move-2.2.sh:  An error occurred within chroot
wubi-move-2.2.sh:  Error is: E: Sub-process /usr/bin/dpkg returned an error code (1)
wubi-move-2.2.sh:  Attempting to exit chroot normally...
wubi-move-2.2.sh:  Exiting from chroot on target install...

wubi-move-2.2.sh:  Migration did not complete successfully.[/COLOR]

```

I tried Googling but the error seems too ambiguous to pull up anything helpful to my situation. Thanks in advance for any help!

---

### Post by bcbc on 2012-07-02
It sounds like you have some broken dependencies (or some other packaging error). Please can you post the output of:
```
sudo apt-get install -f
```

FYI: (from man apt-get)
>       -f, --fix-broken
           Fix; attempt to correct a system with broken dependencies in place.
           This option, when used with install/remove, can omit any packages
           to permit APT to deduce a likely solution. If packages are
           specified, these have to completely correct the problem. The option
           is sometimes necessary when running APT for the first time; APT
           itself does not allow broken package dependencies to exist on a
           system. It is possible that a system's dependency structure can be
           so corrupt as to require manual intervention (which usually means
           using dselect(1) or dpkg --remove to eliminate some of the
           offending packages). Use of this option together with -m may
           produce an error in some situations. Configuration Item:
           APT::Get::Fix-Broken.


---

### Post by Racer Of All on 2012-07-02
> **bcbc said:**
> It sounds like you have some broken dependencies (or some other packaging error). Please can you post the output of:
```
sudo apt-get install -f
```

FYI: (from man apt-get)

Thanks for the quick reply and sorry for what seems to be a newb question :P

Anyway here is the output of the command you suggested:
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up g15daemon (1.9.5.4-0~svn529gnome15) ...
Starting g15daemon: .../dev/input/uinput not found ...invoke-rc.d: initscript g15daemon, action "start" failed.
dpkg: error processing g15daemon (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 g15daemon
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

The G15daemon is what seems to be causing all the issues (it's a little program that gives some functionality to my Logitech G19) keyboard. I will try to uninstall it and try again see if it fixes the problem.

EDIT: That was the problem, thank you so much! Now to sort out the sound issues xD
Tried to change the tag on the title to [solved] but the forum doesn't let me.

---

### Post by bcbc on 2012-07-02
Great! Glad you got it resolved. Not at all a newb issue (in my opinion).

PS I should have mentioned you can use the --resume option when running the migration so you don't have to copy all the files again. (Otherwise you have to empty the target partition completely). But it sounds like you might have already done that.

---

