---
title: "custom livecd creation problems"
date: 2009-12-17
forum: General Help
---

### Post by tlacuache on 2009-12-17
Greetings,

I'm following the guide at [https://help.ubuntu.com/community/LiveCDCustomizationFromScratch](https://help.ubuntu.com/community/LiveCDCustomizationFromScratch) to create my own LiveCD from scratch.

I would like the LiveCD to be bootable (duh), installable (using Ubiquity) and also USB-installable (using usb-creator-gtk). The guide indicates that each of those should work.

I followed all the steps as indicated. At the point where the guide says "Next, you may install more packages as you like" I did apt-get update, apt-get upgrade, apt-get dist-upgrade to update all my packages and then I proceeded to use apt-get install to install the packages I wanted included in the LiveCD (including the base packages for a very minimal desktop installation, similar to this other guide: [http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)). I then followed the rest of the procedure to finish with the ISO generation.

The LiveCD ISO boots fine, but there are three problems:

1. For some reason it boots to the command line prompt (ubuntu@ubuntu:~$) instead of starting X. It's not a problem with X itself, because if i do "sudo gdm" it starts up fine just like a LiveCD should. I don't really care about this issue, but it is curious.

2. Running the "USB Startup Disk Creator" give me an error window which says "An error occurred while talking to the DeviceKit-disks service." Running it from the command line, with or without sudo, gives the same error.

3. Running the "Install Ubuntu" icon on the desktop provides no visible results at all, and running "ubiquity gtk-ui" from the command line (with or without sudo), gives me: "Inhibit all polling failed: Failed to execute program /lib/dbus-1.0/dbus-daemon-launch-helper: Success".

I have a feeling problems 2 and 3 are related, but I'm not sure how, exactly.

Any ideas would be appreciated!

-SG

---

### Post by tlacuache on 2009-12-18
I started from scratch again and rather than installing no packages and then adding them, I installed ubuntu-desktop and then removed the packages I didn't want (openoffice, evolution, etc.).

This worked. So apparently there were some packages I needed that didn't get installed.

---

### Post by netroy123 on 2010-01-17
you just needed to install **ubiquity-frontend-debconf**

---

