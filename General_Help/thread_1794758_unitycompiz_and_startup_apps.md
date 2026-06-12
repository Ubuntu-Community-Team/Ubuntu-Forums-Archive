---
title: "unity/compiz and startup apps"
date: 2011-07-01
forum: General Help
---

### Post by dld on 2011-07-01
Ok! Ok!  I give up; no more trying to make Devilspie run in Unity.  I will switch to compiz programming and I have done that.  Its quite a chore,  But without positive results!!

1)  All my "startup apps" windows pile up on the first workspace, with an occasional exception.  If I then close those windows and restart them from the launch pad most go to the correct workspace and position.   But how do I make compiz place startup windows???????????  

2)  Its strange, but I can't make Chromium stick as a startup app.  Sometimes it will remain after a reboot, but usually it doesn't and therefore chromium-browser doesn't startup at login.  Is there something I should be doing to make it stick?

---

### Post by 3Miro on 2011-07-01
Devilspie is build on top of Metacity and hence it works only with Metacity. There is no way to make Devilspie work with compiz or any other WM.

Unity if build as a plugin for compiz and the whole things stands on top of same old Gnome 2. You can use "startup applications" to make chromium start by default (find it in the global menu, it should be under System -> Preferences).

As for the first question, compiz is a bit strange when it comes to workspaces. In a way, compiz "thinks" of workspaces as one continuous wall and thus sometimes it cannot properly distinguish between them. Basically, I don't know the answer to your first question.

---

### Post by dld on 2011-07-01
Thanks for the explanation.  Devilspie is gone from my Unity version of 11.04.

I have entered /usr/bin/chromium-browser  as a startup app using SystemSettings->StartupApplications many times.  My problem is that it does not remain on that list through a reboot.   I enter it.   I go back into SystemSettings and look and its there.   Then I reboot and it is generally gone; I have seen it stay through one or two reboots.  But its not reliable.

---

### Post by dld on 2011-07-02
Well, I have a solution; hopefully its temporary.  I wrote the following:

#!/bin/bash
sleep 10
/usr/bin/gnome-terminal &
/usr/local/seamonkey/seamonkey &
/usr/bin/chromium-browser &
/usr/games/sol --freecell &

and put it in as a Startup App.  Took terminal, seamonkey, chromium, freecell out as Startup Apps.  Compiz still refused to place as I want.  Navigator would not go to workspace 2, so I had to put the Seamonkey windows in workspace 1 and the terminal in 2.   Its hard to believe that Canonical is going to push Unity on us without 'classic' in October.

---

