---
title: "X loading on a non existent tty?"
date: 2011-01-18
forum: General Help
---

### Post by iceman_ch on 2011-01-18
I've got a weird problem.  I'm running Ubuntu 10.10.  When it starts up sometime I will get a low-graphics x-server error message.  It says that the setting can't be detected.  IF I tell it to reset it will come up with the same error.  If I tell it to cancel it will exit to tty2.  Here is the weird part.  If I switch to tty7 where x should be starting I can see all of th boot post messages.  If I then switch to tty8 which shouldn't really be there at all I get gdm.  I can then log in and everything is normal.  I'm not sure where to start to fix this problem.  I've tried reseting the settings in X-config and Nvidia-settings and neither one works.  I think I need to find the file that tells ubuntu what to start.  That way I can just stop the second x from starting.  Can anyone give me any hints?

---

