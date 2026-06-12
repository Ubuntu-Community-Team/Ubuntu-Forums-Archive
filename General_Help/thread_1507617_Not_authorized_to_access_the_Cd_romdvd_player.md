---
title: "Not authorized to access the Cd rom/dvd player"
date: 2010-06-11
forum: General Help
---

### Post by marcoftheknight on 2010-06-11
Running Ubuntu Lucid 10.01 Have you recently made an upgrade to your system and maybe like me you allow unstable upgrades?

Well here's the code you need to get your dvd rom working again if someone would like to explain the code please feel free because I dont feel like figuring it out I pretty sure it means write over files that have to do with the dvd rom directory. If someone knows why this happen what causes it I would be curious to know.

CODE: sudo ln -s /dev/cdrom /dev/dvd

Thanks

---

### Post by andrewc6l on 2010-06-11
This code creates a symbolic link called /dev/dvd that points to /dev/cdrom. I'm not sure that will survive a reboot, though - you might need to make a udev rule to do it every time.

Look in /etc/udev/rules.d for a rule for your CDROM. You can then add a SYMLINK+="dvd" to have it create /dev/dvd automatically for you.

Here's the advanced documentation:
[http://reactivated.net/writing_udev_rules.html](http://reactivated.net/writing_udev_rules.html)

---

