---
title: "Ubuntu 10.10 upgrade failed?"
date: 2010-11-21
forum: General Help
---

### Post by ThatLucidGuy12 on 2010-11-21
So I decided to upgrade Ubuntu to 10.10. OK, that went well, fine, until I rebooted. I told it to boot to Ubuntu (i'm using Wubi) but now instead of GRUB I get this crap:
[something]No wubildr (this usually happens)
[something]

Then the screen clears and now here's the scary stuff:

error, file not found
error, file not found
error, no suitable device found

Help? Don't want to re-install Wubi and I can't burn any Live CDs as of now.

---

### Post by bcbc on 2010-11-21
> **ThatLucidGuy12 said:**
> So I decided to upgrade Ubuntu to 10.10. OK, that went well, fine, until I rebooted. I told it to boot to Ubuntu (i'm using Wubi) but now instead of GRUB I get this crap:
[something]No wubildr (this usually happens)
[something]

Then the screen clears and now here's the scary stuff:

error, file not found
error, file not found
error, no suitable device found

Help? Don't want to re-install Wubi and I can't burn any Live CDs as of now.

Copy the c:\ubuntu\winboot\wubildr file over the c:\wubildr file.

PS ... bug report:[https://bugs.launchpad.net/wubi/+bug/653134](https://bugs.launchpad.net/wubi/+bug/653134)

---

### Post by ThatLucidGuy12 on 2010-11-21
Thanks, rebooting to try that out.

---

### Post by ThatLucidGuy12 on 2010-11-21
No, but it does seem to have helped a little bit. Now it doesn't throw up any errors, but the machine just reboots. I also noticed C:\ubuntu\disks\boot\grub\ was empty. Could that be it?

---

### Post by bcbc on 2010-11-21
No boot/grub is always empty.

Usually that workaround fixes the problem...:confused: the only alternative I know is to boot a live CD, loop mount the wubi root.disk and manually edit grub.cfg.

Here's a link to the original "workaround" description [http://ubuntuforums.org/showpost.php?p=9932369&postcount=5](http://ubuntuforums.org/showpost.php?p=9932369&postcount=5)

PS... if you need to get data off the root.disk from windows you can use a tool called [ext2read]("http://ext2read.blogspot.com/").

---

### Post by ThatLucidGuy12 on 2010-11-21
OK, got the data off it. Like I said I can't burn a Live CD right now so I'm gonna reinstall Wubi.

---

