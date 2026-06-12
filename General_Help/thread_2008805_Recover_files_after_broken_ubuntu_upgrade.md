---
title: "Recover files after broken ubuntu upgrade"
date: 2012-06-23
forum: General Help
---

### Post by Margaret Dumont on 2012-06-23
Dear all,

I had an Ubuntu 10.04 LTS installed an running in my laptop.

I tried to upgrade it to the next LTS 12.04 through the command: ```
update-manager -d
``` Unfortunately, I left it unattended and the computer shut down while I was away.

I tried to resume the install but it yield many many errors (mainly  dependence errors, packages that yielded errors are listed below). 

Now it doesn't boot anymore. It says "The disk / is not ready or not  present - Keep waiting, press S to omit mounting or M to carry out a  manual recovery"

Pressing S doesn't do anything, and pressing M brings me to a system  promp saying "Root filesystem check failed. A maintenace shell will now  be started." but I don't know what can I do from there because the files in the home folder of my old user don't show up.

My idea was to copy all my important files and just do a clean install.  The problem is that I have tried booting from an Ubuntu 10.04 LTS Live  CD and I can see my folders and everything but I cannot access a few of  them due to permission problems. Since I do not have permission to read  those, I cannot make a backup copy of my files, so I can't do a clean  install, which would be the easiest way to go.

I tried creating a user within the Live Ubuntu with the same name and  password to see if then I could access my files but it won't let me  because it complains that the password is too short (the original one  was just four letters and the minimum now is six).

I have tried booting from Hiren's Boot CD, which has been very useful to  me in other occasions, but the Mini Windows tells me that the  partitions of interest are not formatted, and the Mini Linux doesn't  boot at all, which is surprising to me because it was running smoothly  in previous occasions. It starts loading but then it gets stuck in a  black screen.

Then I decided that maybe I shoud try to fix the broken upgrade after  all and downloaded the Alternate CD of the Ubuntu 12.04 LTS  distribution, but running the "Rescue a non functional system" option  just brings me again with the blank screen.

Does anyone have any idea on how I can copy all my files to have a backup before I just start from the beginning?

Thank you in advance!

-------------

These are the packages that gave dependence or configuration errors during install:

ifupdown, upstart, udev, plymouth, mountall, initscripts,  wpersupplicant, initramfs-tools, network-manager, gnomebluetooth,  friendly-recovery, netbase, dbus, dbus-x11, gconf2, libcompizconfig0,  /var/cache/apt/archives/hostname_3.06ubuntu1_amd64.deb, hostname,  /var/cache/apt/archives/resolvconf_1.63ubuntu14_all.deb,  keboard-configuration, console-setup, kbd, xserver-xorg-core

Perhaps a problem with "mountall" is preventing my root folder to mount properly?

---

### Post by d.atanasov on 2012-06-23
Hi, 

When you tried to copy the files while you where in LiveCD of Ubuntu did you tried to be root (simply sudo su and it does not ask you for password)? If yes sorry for asking :) I will think for something else later...

---

### Post by Margaret Dumont on 2012-06-23
Dear D. Atanasov,

Actually, I didn't... silly me!  xD

I've tried it now through typing in the terminal: ```
sudo nautilus
```

I could't find my folders at first but then I realised that it was simply that the partitions weren't mounted. Once I did that (just clicking on the partitions in the non-sudoed nautilus), I could backup my files without any problem.

Thank you very much for your reply!    :)

---

### Post by d.atanasov on 2012-06-23
I am glad that I could help. I was many times in the same position like you.  So enjoy your new ubuntu on the way :)

---

