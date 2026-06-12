---
title: "Applications Startup problem"
date: 2010-04-23
forum: General Help
---

### Post by vzhen on 2010-04-23
Ubuntu 9.04
Dell inspiron 1501


Problem:Startup applications unable to disable or duplicate startup


Last time, i set up 3 applications to automatic startup kmess stardict and skype and i tick "Automatically remember running applications when logging out".After reboot, 3 of the applications duplicate start which mean  2xkmess  2xstardict  2xskype.

Now, i remove all the manually set up applications and uncheck "Automatically remember running applications when logging out" but 3 of them still automatically start (no more duplicate)

So my question is how do i disable those manually set up startup and will not duplicate startup.

-------------------------------------------------------------------------

Reason: After turn off saved session still go back to previous session
Answer:remove all the files under saved-session folder
#rm -R ~/.config/gnome-session/saved-session



Thanks

---

