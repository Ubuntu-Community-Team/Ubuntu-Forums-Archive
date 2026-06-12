---
title: "can't access mounted drive?"
date: 2010-08-28
forum: General Help
---

### Post by polardude1983 on 2010-08-28
Ok so I have a drive called Extra Hard Drive and somehow I can't access it. Anyways posting screenshots

[IMG]http://i.imgur.com/BWiBl.png[/IMG]

[IMG]http://i.imgur.com/iEmUb.png[/IMG]

---

### Post by Morbius1 on 2010-08-28
When you say you can't access it do you mean you can't go to File System > /mnt/mydrive ?

Or do you mean it's not showing up under Places?

It it's the latter, any mountpoint in /home/username or /media will produce a mount icon on the desktop and show up under Places. Any mountpoint in /mnt or off the root directory itself ( "/" ) will not produce a desktop icon and not show up under Places.

If you want it to show up under Places you have two options:

Change the mountpoint from /mnt/mydrive to /media/mydrive

Or go to /mnt/mydrive in Nautilus and Bookmark it: Bookmarks > Add Bookmark

---

### Post by houndi on 2010-08-28
change the device settings if it is not visible. if it is not accessed need to change the settings when you start OS

---

### Post by polardude1983 on 2010-08-29
> **Morbius1 said:**
> When you say you can't access it do you mean you can't go to File System > /mnt/mydrive ?

Or do you mean it's not showing up under Places?

It it's the latter, any mountpoint in /home/username or /media will produce a mount icon on the desktop and show up under Places. Any mountpoint in /mnt or off the root directory itself ( "/" ) will not produce a desktop icon and not show up under Places.

If you want it to show up under Places you have two options:

Change the mountpoint from /mnt/mydrive to /media/mydrive

Or go to /mnt/mydrive in Nautilus and Bookmark it: Bookmarks > Add Bookmark

YOU ARE AWESOME! I have posted this question before and before, and only you answered it. AWESOME. It is mounted i wonder if it will stay mounted next restart. anyways thankx!

---

