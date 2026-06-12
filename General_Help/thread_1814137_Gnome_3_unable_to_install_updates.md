---
title: "Gnome 3 unable to install updates"
date: 2011-07-29
forum: General Help
---

### Post by miasmablk on 2011-07-29
So I've had these three packages in my updates manager for about 3 days now that I have been unable to select and install i'm running gnome 3 on a natty 64 bit install. normally these things tend to fix themselves but this doesn't seem to want to go away. I've already tried removing to ppa and then re-adding.. and sudo dpkg --configure -a i'm not really sure what to do as i'm pretty much a noob at all of this..

[http://ubuntuforums.org/picture.php?albumid=2382&pictureid=8057](http://ubuntuforums.org/picture.php?albumid=2382&pictureid=8057)

---

### Post by vhook on 2011-07-29
There are two things you can try. I recommend install aptitude (sudo apt-get install aptitude) and then doing sudo aptitude safe-upgrade. If you don't want to install aptitude, you can do sudo apt-get dist-upgrade, but read what it says before you hit yes. It may try and remove some packages that are vital. Aptitude tends to handle these things better from my experience.

---

### Post by wildmanne39 on 2011-07-29
Hi, to be able to help you with this issue we need you to run this command in a terminal
```
sudo apt-get update && sudo apt-get upgrade
```
and post the error messages back here by clicking on new reply and click # and paste the information between the brackets.

---

### Post by miasmablk on 2011-07-29
thank you..fixed it with aptitude

---

### Post by wildmanne39 on 2011-07-29
Hi, I am glad you got it fixed.

---

