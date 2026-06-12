---
title: "CD ROM drives listed multiple times"
date: 2009-07-28
forum: General Help
---

### Post by dkolars on 2009-07-28
Have been using Ubuntu (Jaunty) for about 3 weeks now...  still learning as I go...

Just set up Grip for ripping CD's to replace the AudioGrabber I was used to in Windows...  Using GNOME Commander, I see that I have the following CD/DVD drives:

cdrom
cdrom0
cdrom1
cdrom2
cdrom3

Interesting, as I only have 3 drives... so, I did a 'sudo eject xxx' and discovered that:
-- cdrom and cdrom1 are the external DVD player/burner;
-- cdrom0 and cdrom3 are the internal CD/DVD player;
-- cdrom2 is the internal DVD player/burner.

Why are there multiple listings for the same drives?  Perhaps because they are both CD & DVD?  Player & burner?  That's the only reason I can think of...

I would guess that having them listed doesn't really add a lot to the system overhead, so no need to worry about "tidying up" and deleting any unnecessary listings of media... they seem to all function just fine.

Thanks!

---

