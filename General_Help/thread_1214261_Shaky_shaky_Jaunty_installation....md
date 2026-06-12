---
title: "Shaky shaky Jaunty installation...??"
date: 2009-07-15
forum: General Help
---

### Post by cfogelberg on 2009-07-15
Hi all,

My Jaunty installation seems to have become really shaky, matlab has just stopped starting and the update behaviour is very strange too. Plus, when I log in I get a "your .dmrc file has the wrong permissions error". Details and chronology are as follows. Any suggestions on how to fix it much appreciated!!

1) Some time ago I wanted Amarok 2.1 (I hoped for functionality), and so I followed the instructions on the amarok webpage ([http://www.kubuntu.org/news/amarok-2.1](http://www.kubuntu.org/news/amarok-2.1))

2) Amarok 2.1 started working really well but very quickly became only semi-functional - I can't edit the id3 tags using amarok anymore and the dynamic play lists mostly don't work and last.fm only works sort of now. I don't know what could have caused this.

3) After a few weeks I ran apt-get update and apt-get upgrade and upgraded everything. Now the Update Manager keeps popping up telling me there are lots of updates to install (although when I run apt-get from the command line there isn't anything).

The itemised list of problems right now is:
* Amarok semi-functional, as described above
* Update Manager likes to tell me to update, so far I've ignored it
* Matlab doesn't work. When I start it the process clearly starts but the splash screen is never displayed. I don't know why it doesn't work.
* When I log on (e.g. after rebooting) I get a warning message, something along the lines of: "Warning: $HOME/.dmrc permissions are incorrect, it must have permissions 0644". However the file ~/.dmrc does have permissions 0644, and the same problem occurs if I set its permissions to 0666 even.

If anyone has any suggestions or tips they'd be much appreciated! Likewise, if you want any more info please just ask :)

Thanks,
Christo

---

### Post by coffeecat on 2009-07-15
**Solving .dmrc and $HOME Permission Errors:**

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

You also need to reset your $HOME permissions.

---

### Post by cfogelberg on 2009-07-16
That has fixed the .dmrc problem but not the matlab problem or amarok problems. Any further suggestions much appreciated!! :)

xto

---

