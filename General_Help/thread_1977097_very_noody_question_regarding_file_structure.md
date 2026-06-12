---
title: "very noody question regarding file structure"
date: 2012-05-09
forum: General Help
---

### Post by snig on 2012-05-09
Hello I'm very new to Ubuntu and i have been a windows boy all my life. I wish to make the transition but I'm a little confused about how the files are ordered. i understand the concept of the root directory but nothing after that, things like var and usr. where would my programs be held. another thing that's bothering me is that as a user when I place my files in my directory home/user/ they seem to be appearing on the desktop and I don't think that's normal. if someone could try and answer my 2 questions I would be very grateful.
many thanks.

---

### Post by Vaphell on 2012-05-09
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

your desktop should be /home/yourname/Desktop (or localized version of Desktop, depending on language), it is weird that files in /home/yourname appear on desktop

---

### Post by snig on 2012-05-09
thanks and I know i had a Desktop folder but even that appeared on the actual desktop so i deleted i know i should keep it and i can restore it

---

### Post by PaulW2U on 2012-05-09
[http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard](http://en.wikipedia.org/wiki/Filesystem_Hierarchy_Standard) explains the file system structure quite nicely.

---

### Post by Vaphell on 2012-05-09
run terminal with ctrl+alt+t
```
grep DESKTOP .config/usr-dirs.dirs
```
what does it say?

---

### Post by snig on 2012-05-09
i just fixed the desktop problem it was because I deleted it the plasma work station setting displayed the next level up which was home/myname i just put the desktop folder back in and repointed it :) also i will take a look at all of those links later on thanks so much guys/gals

---

### Post by kostkon on 2012-05-09
> **snig said:**
> i just fixed the desktop problem it was because I deleted it the plasma work station setting displayed the next level up which was home/myname i just put the desktop folder back in and repointed it :) also i will take a look at all of those links later on thanks so much guys/gals
You are using Kubuntu then?

Anyway, I just wanted to say that, generally, as a simple user you only need to care about your home folder, i.e. /home/yourusername

---

