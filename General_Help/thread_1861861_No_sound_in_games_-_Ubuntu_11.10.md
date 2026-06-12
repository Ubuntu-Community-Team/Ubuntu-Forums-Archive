---
title: "No sound in games - Ubuntu 11.10"
date: 2011-10-16
forum: General Help
---

### Post by lukebargh106 on 2011-10-16
Hey,
My problem is that I'm trying to play Wolfenstein: Enemy Territory as well as King Arthur's Gold. I can listen to music on Banshee and other stuff, But when I load the game up, there is no music, no sound.. Nothing.

I don't know how to fix this, so any help would be deeply appreciated.

Regards-
Luke.

---

### Post by cottfcfan on 2011-10-16
This could be a duplicate of the problem here:
[http://ubuntuforums.org/showthread.php?t=1861838](http://ubuntuforums.org/showthread.php?t=1861838)
I'm looking for a solution as well.
Please try something for me.
Open Aisletot Solitaire & enable sounds in the control Tab. When you move the cards do you get any sound or not?
Also does Music play in Banshee or not?

---

### Post by benguela on 2011-10-20
I have the same problem, no sound in games, e.g. Astromenace
No sounds in Aisletiot Solitaire after turning on in control tab.
Music does play Banshee.

---

### Post by cottfcfan on 2011-10-20
So is this just the way Gnome 3 is?
Could it be a bug?
Does anyone have any sound at all in games etc?
Feedback would be appreciated.

---

### Post by cottfcfan on 2011-10-22
Found a solution to my sound issues:
1st. Install dconf-editor
Then open it from applications and navigate to:
org/gnome/desktop/sounds.
Make sure event sounds & input feedback sounds are both ticked & change theme name to ubuntu.
Done.

---

