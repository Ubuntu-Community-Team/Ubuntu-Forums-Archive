---
title: "Unreadable files in /dev --- problem??"
date: 2011-06-09
forum: General Help
---

### Post by tomkat3 on 2011-06-09
Hello everybody!

For the last two weeks I've had lots of problems with my computer, I think related to my nVidia graphics driver, see [here]("http://ubuntuforums.org/showthread.php?t=1772679").

Basically, this has required me to force restart my computer whenever something causes my computer to freeze: graphics driver or gnome, or the X server, I'm a newbie so I don't really know what the problem is. Help!

I looked into the /dev folder today to find nvidia0 (I saw an error message once that said that it couldn't open it...), and there were TONS of files marked as unreadable/unknown file type. There were files called tty up to 63, ram up to 15, and vcsa up to vcsa7...etc. 

I saw [this]("http://ubuntuforums.org/showthread.php?t=744693") thread when I googled my problem, and I'm worried about the effect all these force restarts are having on my computer. I can't imagine this is a good thing, how do I stop/fix this?

Come to think of it, I didn't start seeing the 'blue mist' mentioned in my other thread until I force restarted the graphically demanding program that froze everything. Could this be the source of my problem?

---

### Post by FormatSeize on 2011-06-09
> **tomkat3 said:**
> I looked into the /dev folder today to find nvidia0 (I saw an error message once that said that it couldn't open it...), and there were TONS of files marked as unreadable/unknown file type. There were files called tty up to 63, ram up to 15, and vcsa up to vcsa7...etc. 

This is normal, and does not pose a problem. And trying to open the nvidia0 file and not being able to isn't an error. That would be like me trying to open my sr0 file. I would have to ask myself, "If I open this file that is actually that there DVD optical drive, what would I expect to see?"
 
The thing is, Linux takes everything to be a file. So while things appear on the system as files as we traditionally think of them (things with human-readable words in them) they may physically be a drive, card, usb, or other device.
 
EDIT: After a quick re-read, if it was your computer saying that it couldn't open your nvidia0 file, that's a problem with the card or drivers.

---

