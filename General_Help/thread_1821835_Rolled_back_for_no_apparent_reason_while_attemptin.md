---
title: "Rolled back for no apparent reason while attempting a hard drive migration."
date: 2011-08-09
forum: General Help
---

### Post by jakerman999 on 2011-08-09
Earlier today I was trying to move my Ubuntu installation to a larger hard drive via the method at [http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/) .  The command dd hung for no reason, and after a long while spewed out various errors about processes not responding for more than 120 seconds(this wasn't until roughly an hour though).  Giving up, I rebooted into my old hard drive, and discovered that everything I've done in the past three days, including software installed, files downloaded, and local changes has been erased as if the computer had rolled back, or never even been used.

Can anyone tell me either how or why this occurred, or how to undo(read: redo) this?

---

### Post by dcstar on 2011-08-10
> **jakerman999 said:**
> Earlier today I was trying to move my Ubuntu installation to a larger hard drive via the method at [http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/](http://www.arsgeek.com/2008/01/22/how-to-clone-your-bootable-ubuntu-install-to-another-drive/) .  The command dd hung for no reason, and after a long while spewed out various errors about processes not responding for more than 120 seconds(this wasn't until roughly an hour though).  Giving up, I rebooted into my old hard drive, and discovered that everything I've done in the past three days, including software installed, files downloaded, and local changes has been erased as if the computer had rolled back, or never even been used.

Can anyone tell me either how or why this occurred, or how to undo(read: redo) this?

[LIST=1]
[*]**dd** does not work well with drives with bad blocks, you should be using **ddrescue**.
[*]dd is a READ ONLY process as far as the source drive is concerned, but if your hardware died or your source disk has bad blocks then problems like yours can occur as the system tries to repair itself on the next boot.
[*]Try not to use old "HOWTOs" that do not apply to your current version, you can get into trouble because things change over time.
[/LIST]

---

### Post by jakerman999 on 2011-08-10
As far as I know, the drive isn't damaged.  I just wanted to migrate to a drive with a larger capacity without having to redo all the configuration changes, software and file downloads, etc.

is there another, possibly easier way of doing this?

---

