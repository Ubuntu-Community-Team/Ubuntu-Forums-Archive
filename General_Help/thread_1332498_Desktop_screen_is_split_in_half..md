---
title: "Desktop screen is split in half."
date: 2009-11-20
forum: General Help
---

### Post by Mestas on 2009-11-20
For whatever reason today when I turned on my PC the desktop is split in half, and it only does this for my user. I haven't changed any settings that I know of in the last week or so. I'm using 9.10 , any help is appreciated.

---

### Post by P4man on 2009-11-20
thats the weirdest thing Ive seen in a while.. looks like graphical corruption with that icon being multiplied 100's of times. Problem with videocard overheating?

What videocard do you have and what drivers? Are you running desktop effects?

---

### Post by Mestas on 2009-11-20
I have a Nvidia 6600, and the drivers are 185.18.36.
It's only corrupt like that when compiz is enabled but even with none of the effects on the screen is still split down the middle, and all those icons are there because whatever is on that side of the screen gets imprinted there until something else comes along.

---

### Post by P4man on 2009-11-20
Ive never seen anything like it. And you have a very common videocard with the same drivers everyone else uses. Im leaning towards a hardware problem with the videocard but perhaps someone has other suggestions...

---

### Post by Mestas on 2009-11-20
It could be hardware but the screen is only like this on my user account so some setting that became corrupt must be doing it.

---

### Post by emigrant on 2009-11-20
since this problem is only for one user, how about replacing .nautilus with another users?

---

### Post by P4man on 2009-11-20
hmm.. is that gnome-do as dock? Have you tried disabling it?
If all else fails, make a new user and copy the stuff you need over to the new users's home.

---

### Post by Mestas on 2009-11-20
Well, I'm not too sure what just happened but it's fixed, all i did was make a new user and switched to it, and when i came back to my usual account it was fixed.

---

### Post by El King on 2009-11-24
> **Mestas said:**
> Well, I'm not too sure what just happened but it's fixed, all i did was make a new user and switched to it, and when i came back to my usual account it was fixed.

i have the same problem, but ur solution didn't fix it ! :(

---

### Post by mctt on 2013-03-22
Found a fix that worked for me:
1. Open nautilus, Home Dir.
2. CTRL+H (Show hidden folders).
3. Select all except Desktop.
4. CTRL+X
5. Nautilus to Desktop, create folder. Paste into folder.
6. Found it stopped and the screen restarted fixing the problem.
7. The copy process stopped with .compiz, so I figure the problem is there.

---

