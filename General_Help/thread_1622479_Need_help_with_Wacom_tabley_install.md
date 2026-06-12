---
title: "Need help with Wacom tabley install"
date: 2010-11-15
forum: General Help
---

### Post by duoc9119 on 2010-11-15
I was following this [http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html](http://www.ubuntugeek.com/wacom-bamboo-ctl-460-in-ubuntu-10-04-lucid-lynx.html) to install my tablet but replaced all 0.8.6 with the latest 0.8.8-10 and it was going good until i got to the sudo rmmod wacom. I just get an error.

I don't remember what it said but I closed out of terminal. Is there a way to uninstall what I have done or does it not install all the way since I didn't finish?

I'm real new with Linux so I'm sort of clueless

---

### Post by Favux on 2010-11-15
Hi duoc9119,

Welcome to Ubuntu forums!

Are you in Lucid or Maverick?  The only change you should have made to the system files was replacing the default wacom.ko (the usb kernel driver) with your newly compiled wacom.ko.  That's what the copy (cp) command was about.  And the sudo made you super user or root so you could change the system file, otherwise you wouldn't have had permission.

As you figured out posting the error helps identify the problem.  Anyway try the [Bamboo P&T HOW TO]("http://ubuntuforums.org/showpost.php?p=9496609&postcount=1").

---

