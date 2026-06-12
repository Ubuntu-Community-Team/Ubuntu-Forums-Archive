---
title: "Scripted reset of file permissions?"
date: 2011-01-16
forum: General Help
---

### Post by Saidear on 2011-01-16
I have 4 directories shared on my server that are accessed by Windows machines.  Problem is that the windows machines 'Lock' the file on the server so I can't access them from another machine.

What I'd like is a simple way to have the following commands run every 2 hours or so:

sudo chmod -R 777 /home/user/Videos
sudo chmod -R 777 /home/user/Downloads
sudo chmod -R 777 /home/user/Music
sudo chmod -R 777 /media/Movies

Any ideas on how I could do this?

---

