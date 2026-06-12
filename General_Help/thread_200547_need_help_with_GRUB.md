---
title: "need help with GRUB"
date: 2006-06-20
forum: General Help
---

### Post by nickdr on 2006-06-20
i am very much a linux nOOb, so please dumb down any help you can give.

i am going to reinstall windows xp in a matter of hours (just something i do twice a year to keep it fast and clean) and right now i am dual booting with ubuntu. after windows is reinstalled how can i restore ubuntu so that i can dual boot again??

i would just reinstall ubuntu but i had this amazing streak of luck where i finally (after like 3 months of trying) got my wifi working, and that i wont risk again.

thanks again for the help.

---

### Post by x64Jimbo on 2006-06-20
Backup your MBR. This can be done with the "partimage" tool. When it asks you what partition you want to back up, you select /dev/hda or whatever your hard disk device is WITHOUT a number on the end. The number signifies the partition number, and if you leave that off, it chooses the MBR. Once you've done that, reinstall windows. Once that's done, boot from a livecd that has partimage. Not sure if ubuntu has it in livecd, but i know for a fact that Kanotix does. Run the same tool and restore the backed up MBR to the hard disk. It should get everything back running smoothly.

---

### Post by givré on 2006-06-20
You could also following this howto [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

