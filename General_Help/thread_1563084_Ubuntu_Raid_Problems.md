---
title: "Ubuntu Raid Problems"
date: 2010-08-28
forum: General Help
---

### Post by donthem on 2010-08-28
Hello,

I'm trying to set up a simple nas server with some softraid 1 and iscsi in Ubuntu 10.04.  I create the raid 1 at install, get the iscsi up and running and everything works fine, for a while.

After about 4-5 reboots the raid is degraded and can only find one harddrive.  I think this is because I am using the onboard sata as well as a pcie sata controller and on reboot the harddrives get relabeled (ie /dev/sda becomes /dev/sdb).  Is this common and is there a config where I can change it to use the uuid?

Also does it make sense the share the drive with iscsi then set the raid up on the client side, in this case osx?

Thanks

---

