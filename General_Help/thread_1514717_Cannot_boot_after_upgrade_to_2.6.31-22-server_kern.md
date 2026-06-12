---
title: "Cannot boot after upgrade to 2.6.31-22-server kernel"
date: 2010-06-21
forum: General Help
---

### Post by johnsample on 2010-06-21
Hi,

Our server requested I update to the latest version of the O/S, I did so, but when it asked me to restart I rebooted and I now get the Ubuntu logo briefly followed by just a black screen (no response, regardless of what I press, including ESC).

If I go into recovery mode I get the following errors (photo here):

[http://i871.photobucket.com/albums/ab273/displaydigital/photo.jpg]("http://i871.photobucket.com/albums/ab273/displaydigital/photo.jpg")

I've tried booting into the older version of the kernel but this doesn't work either. It dumps me out to a command line.

This is a work server and I urgently need to get it up and running again so I can access the files on there. Please help!

Thanks,
John

---

### Post by johnsample on 2010-06-21
Managed to fix this. CTRL-ALT-F1 brought up the terminal, then fsck -y fixed disk errors. Now boots fine.

---

