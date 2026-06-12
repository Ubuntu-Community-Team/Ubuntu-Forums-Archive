---
title: "Cannot Get CD Drive to Open even after Restart"
date: 2010-01-06
forum: General Help
---

### Post by Rob@ThePCWiz.info on 2010-01-06
This is the error message i get. Keep in mind I am running KUbuntu 9.04, after an upgrade from 8.10.
```

rob@node69:~/Documents$ eject cdrom
umount: /media/cdrom0: device is busy.
        (In some cases useful info about processes that use
         the device is found by lsof(8) or fuser(1))
eject: unmount of `/media/cdrom0' failed
rob@node69:~/Documents$ 

```

---

### Post by mechro on 2010-01-06
Does **sudo eject** work?

---

### Post by derekmbarnes on 2010-01-06
Have you tried ejecting the CD manually? Look at the front of your drive; there should be a little hole just big enough to insert the end of a paper clip.

If this is a persistent problem and not just a one-time issue, get back to us.

---

### Post by Rob@ThePCWiz.info on 2010-01-06
sudo does not work. and the pin in my drive is already pressed down, this has happend ONE time before, right after an update to 8.10

---

### Post by 3rdalbum on 2010-01-06
I'm betting you've had a problem with a faulty disc confusing your drive. The solution is to shut down entirely, this kills all power to the drive. When you start up again, keep hammering the "open" button until it comes out.

---

### Post by Rob@ThePCWiz.info on 2010-01-07
not one of my best moments... I'm not sure what happened, but after a few hours, (after I had just said "screw it, I'll deal with it later!") I had forgotten about it, and went to go put another cd in, and it opened right up for me.
 An Explanation would be nice, but for now, this is solved.

---

