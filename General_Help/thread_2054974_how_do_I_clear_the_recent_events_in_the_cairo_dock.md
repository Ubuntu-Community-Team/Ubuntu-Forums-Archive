---
title: "how do I clear the recent events in the cairo dock"
date: 2012-09-08
forum: General Help
---

### Post by supernater on 2012-09-08
I'm running Ubuntu 12.04 using cinnamon.  I installed Cairo Dock and I noticed a icon on it called "Recent Events".  I have two quesitons...

#1
How do I clear this?  If I right click and select "Delete All Events", it will ONLY delete 999 events.  I would have to do this hundreds of times to clear it all, which would be inconvenient.

#2
Where is this information stored on my machine?  What file or directory holds it?

---

### Post by supernater on 2012-09-08
Found the answer.

The activity displayed in the Recent Events applet is data that was being logged by zeitgeist.  I removed the following packages...

python-zeitgeist 
zeitgeist-datahub 
zeitgeist 
zeitgeist-core

Removing them required that I also remove....

unity-lens-video
unity-scope-video-remote
activity-log-manager-control-center
activity-log-manager-common

Then I deleted the /home/supernater/.local/share/zeitgeist folder.  Now the government won't be able to track me :D

NOTE:
This seems to work fine for me because I'm running Cinnamon.  I'm not sure what this will do to Unity or Gnome shell users.

---

