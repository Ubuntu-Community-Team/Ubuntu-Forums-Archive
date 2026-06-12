---
title: "How to Make Ubuntu my Primary OS?"
date: 2011-05-17
forum: General Help
---

### Post by AndreaClaire on 2011-05-17
I'm not sure if this is the right place to put this, and I'm sorry if it isn't.

Anyway, I've just installed Ubuntu here in my pc, so I'm getting used to it; and, I'm planning on making it my primary OS. Aside from Ubuntu, I've got Windows 7 installed, I didn't like it, it was kinda buggy, so, I'd like to uninstall it. But I don't know how to uninstall windows 7 without reformatting, because I don't want to lose Ubuntu.
I was actually going to format, and just install Ubuntu by booting, but there's something wrong with my pc because every time I burn the *.iso image file of Ubuntu that I downloaded on the site, it says that it can't read the data on the CD, I've tried it like, five times, using different CD's and burning programs but, no luck. An error message will also appear about 'not being able to read the cd' when I double click it. I even read the page here about burning Ubuntu *.iso into a cd, I did everything step by step but, still no luck.

Hope someone can help me out. :)

---

### Post by btindie on 2011-05-17
It may be that the downloaded ISO is corrupt and you need to verify that it's correct.

See [Verifying disk and data integrity]("https://help.ubuntu.com/community/BurningIsoHowto") HowToMD5SUM.

Depending on how your Ubuntu installation is configured you could just format your old W7 partition as ext4, copy everything from /home to the new partition and have Ubuntu mount that new partition on /home at startup. Giving you all the space that W7 occupied for your own files. You then wouldn't need to do a clean install.

---

