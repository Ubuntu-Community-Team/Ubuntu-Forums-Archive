---
title: "How do I enable kwallet?"
date: 2010-06-02
forum: General Help
---

### Post by spoon_ on 2010-06-02
I accidentally disabled it, but amarok apparently needs it (to store last.fm credentials), and now I can't find how to re-enable it. I'm using normal ubuntu, not kubuntu.

Thanks.

---

### Post by spoon_ on 2010-06-02
Bump!

---

### Post by spoon_ on 2010-06-06
not bump

---

### Post by spiky001 on 2010-06-06
have a look here see if this helps
[http://forum.kde.org/viewtopic.php?f=115&t=81337&start=30](http://forum.kde.org/viewtopic.php?f=115&t=81337&start=30)

---

### Post by spoon_ on 2010-06-06
Thanks, but I looked at that page before making this post! I don't have the line "ignoreWallet=yes". And adding ignoreWallet=true doesn't help, though I'm not sure where it should go (I tried putting it in the LastFM section.

---

### Post by spiky001 on 2010-06-06
There wasn't mch on google abot it have you tried the kde community forum maybe ask in there

---

### Post by spoon_ on 2010-06-12
For posterity, here's how to re-enable kwallet:

- Install the two packages systemsettings and kwalletmanager
- Launch systemsettings from the command line
- In the advanced tab, find KDE wallet and enable it

---

### Post by Derathor on 2010-06-30
Thanks a lot Spoon_, not only your solution worked, It also helped me discover a handy program. Very useful for a newbie Linux user like me :lolflag: . Cheers.

---

### Post by felipemartim on 2010-07-12
Thanks a lot! I had the same problem with amarok and now it works beautifully.

---

