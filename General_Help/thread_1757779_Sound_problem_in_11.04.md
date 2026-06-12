---
title: "Sound problem in 11.04"
date: 2011-05-13
forum: General Help
---

### Post by wordmaster on 2011-05-13
After upgrading to 11.04, both my sound volume and quality are problems. The volume is so low it is hard to hear and the quality when turned all the way up is bad. Even turned all the way up, it is still quite low.

I am running a Soundblaster card and it worked well in 10.X. It is run through a stereo amp and into huge speakers. With 10.x, I never turned the volume very much at all as it would cause pictures to fall off the wall.

I have been through all the options in System/preferences/sound with no joy.
I am running the classic desktop as the Unity desktop is, to me, an unusable mess.

Any and all help appreciated.

---

### Post by kostkon on 2011-05-13
First of all, try deleting your *.pulse* hidden folder, either by opening nautilus, selecting *View &#8594; Show Hidden Folders*, or by giving this command in a terminal:
```
rm -rf ~/.pulse
```
then logout and login again.

---

### Post by wordmaster on 2011-05-13
Thank you very much! I have no idea what deleting that folder did, but it solved the problem!

---

