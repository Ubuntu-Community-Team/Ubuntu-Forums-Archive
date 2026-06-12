---
title: "Restrict local reboot/shutdown"
date: 2011-03-01
forum: General Help
---

### Post by ragnarok189 on 2011-03-01
Hello all,

I am running freenx on a lucid ubuntu server install with ubuntu-desktop installed over that. My problem is that users can click reboot or shutdown and it works, as it should, being a local user. 

How can I prevent users from rebooting or halting the machine from GUI or local terminal? The only way that I want this machine to be rebooted or halted is by ssh running commands as sudo.

Anybody have any experience with this? Or tricks up their sleeve?
Thank you.

---

### Post by aeiah on 2011-03-01
cant really help, but my suggestion is that you just try and get rid of the mechanism for shutting down via the gui. on the command line they'll need sudo, so you just need to make sure they arent in the sudoers file.

i havent got a standard ubuntu install in front of me so i cant check, but perhaps you can easily change user permissions so they cant shut down using the users & groups settings dialog?

you could also try this, but it may have changed since 2008:
[http://wiki.soslug.org/wiki/disabling_shutdown_and_reboot_in_ubuntu](http://wiki.soslug.org/wiki/disabling_shutdown_and_reboot_in_ubuntu)

---

### Post by ragnarok189 on 2011-03-01
Following the information provided by soslug, I found out that on lucid, gdmsetup now only opens the config screen for login configuration. Nothing to do with modifying buttons available to users.

---

### Post by ragnarok189 on 2011-03-03
*bump*

Anybody know of a solution?

---

### Post by ragnarok189 on 2011-03-03
Actually just found the answer.

[http://ubuntuforums.org/showthread.php?t=1670897&page=2]("http://ubuntuforums.org/showthread.php?t=1670897&page=2")

Thank you all for your help though.

---

