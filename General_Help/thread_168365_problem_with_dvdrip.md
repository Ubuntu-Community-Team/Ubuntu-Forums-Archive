---
title: "problem with dvd::rip"
date: 2006-04-30
forum: General Help
---

### Post by harys on 2006-04-30
hi, i have this erro message when i tried to access the tab rip title in dvd::rip : 
An internal exception was thrown!
the error message was :
mkdir/CHANGE_me:Permission denied at /usr/share/perl5/Video/DVDRip/Project.pm line261

thanks for your reply.
harys

---

### Post by Bloch on 2006-04-30
I'm not quite sure.
It looks to me like the program wants to create a directory (mkdir) and doesn't have permission to make a directory in that place.
When you were asked to name a folder for your project when you started dvd::rip, did you choose a folder in your home directory? 

You could also try running it as superuser, i.e. by using the command line
sudo dvdrip

---

### Post by harys on 2006-04-30
hi, thanks for your help i had to change the default directory in edit>preferences to my home directory. now it should work. harys

---

### Post by [pl]ice on 2006-05-01
did it worked???
 just asking couse i'm ripping atm :) try using k9copy to minimize it, then use k3b to burn it...
  i have used b4 dvd decrypter/shrink with wine, worked wicked,but beware, k3b gave me shit lots of problems with settings, make usre u set correctly for dvds u're using (eg R-).
have fun :D

---

