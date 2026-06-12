---
title: "How can i set Xgamma on Ubuntu startup?"
date: 2010-10-07
forum: General Help
---

### Post by SuperUserDO on 2010-10-07
Hi,
i have downloaded Ubuntu 10.04 and installed it successfully,but the problem is the screen is too bright even in windows but i used to adjust the brightness,contrast and gamma in windows by ati catalyst control center,i couldn't install ati catalyst control center in Ubuntu or i installed it but it didn't work maybe because the ATI graphic card is built in,anyway after searching the web i found Xgamma feature and adjusted it to 0.70 and the screen's colors is ok To some extent,but every time i start Ubuntu i have to set it again.
So is there any way to make it permanent or is there any other better way to calibrate my LCD monitor?
Thank You :)

---

### Post by SuperUserDO on 2010-10-07
Hello!!!

---

### Post by UnterUn on 2010-10-07
Hey! 

Can you change the gamma physically on your monitor? - Normally there's a menu button underneath or on the side of the monitor and somewhere in there (the menu) you maybe be able to change the brightness, contrast and/or gamma.

Else try going to 'System' > 'Preferences' > 'Start-up applications' and 'add' the program to start up, on start-up.

Then if you can work out the terminal command to reduce your gamma and such put that in the 'edit' section to automatically run.  Else leave it blank and it will start-up and you can just change it quickly.

Also I just put 'sudo apt-get install xgamma' in the tutorial to try and find out how it works to help and apparently its obsolete in favour of 'x11-xserver-utils', so maybe try that?

---

### Post by SuperUserDO on 2010-10-07
Thank You it worked from System' > 'Preferences' > 'Start-up applications'.
Thanks :):)

---

### Post by Jim_in_Omaha on 2010-12-18
Good Idea. Me Likes!

---

