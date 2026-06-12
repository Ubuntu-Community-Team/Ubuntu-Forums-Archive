---
title: "System crashed, now un-bootable"
date: 2009-08-24
forum: General Help
---

### Post by schwartz on 2009-08-24
My system crashed and now when it boots I end up in busybox.  I'm not sure what to do next.  It looks like maybe I need to fsck the root volumen but I don't see fsck in m list of available commands.

The system is using the disk encryption that you setup when booting off the alternate install CD and it does get through that prompt fine and decrypt the drive.

I have a week old backup that has most of my data, just need to pull a few files off this system os if it's not possible to make it boot I'd be happy if I could at least get it mounted up on another system but I'm not sure how that works with the encryption.

Would appreciate some help:)

thanks,
Bill

---

### Post by zkriesse on 2009-08-24
Can you boot from the Live CD? If so you could try system repair...check these sites out. You might find something at one of them that might help. [HelpUbuntu.com]("https://help.ubuntu.com/") [UbuntuGuide.com]("http://ubuntuguide.org/wiki/Main_Page") and [UbuntuGeek.com]("http://www.ubuntugeek.com/") Hope this helps.

---

### Post by schwartz on 2009-08-24
I found this text in another thread (no answers there) and it's what I'm seeing as well fro busybox

"kinit:name_to_dev_t(/dev/disk/by-uuid/######...)
kinit: trying to resume from /dev/disk/by-uuid/#####...
kinit: No resume image, doing normal boot
mount: mounting /dev on /root/dev failed: No such file or directory
mount: mounting /sys on /root/sys failed: No such file or directory
mount: mounting /proc on /root/proc failed: No such file or directory
Target filesystem doesn't have /sbin/init
No init found. Try passing init=bootarg"


I don't have any ideas what to try next.

Is there a way I can permanently decrypt the drive so I can try to mount it from the live cd?

like I mentioned above the drive is encrypted using the full disk encryption that you setup when installing from the alternate boot cd.  I do get past that part so it can decrypt the drive  before busybox loads and it shows my devices in /dev/mapper


help?

thanks,
Bill

---

