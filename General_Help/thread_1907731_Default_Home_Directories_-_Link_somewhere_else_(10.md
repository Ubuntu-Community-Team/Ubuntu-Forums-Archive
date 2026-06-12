---
title: "Default Home Directories - Link somewhere else? (10.04)"
date: 2012-01-12
forum: General Help
---

### Post by wh33t on 2012-01-12
Hey Forums,

I've got a somewhat strange issue I'd like to figure out. After a regular install of Ubuntu 10.04 I see that there is a bunch of directories made for me in my home directory (Videos, Music, Documents) Is there anyway I can have a directory on my back up drive appear there? I use multiple Operating systems and I transfer files to and from them using a 500gb backup drive. I'd like to have my home directory somehow have a short cut to my back up drive or something similar that will allow me to link the existing Music, Video, Document directories to somewhere on the backup drive.

I think what I'm looking for is something called Symlinking? Kind of like a short cut but different... I apologize for my horrible explanation, but hopefully someone knows what I'm talking about lol.

---

### Post by nonamedotc on 2012-01-12
If you external hard disk is always connected, you could create a folder in your home folder and mount your external HD automatically to that folder.

This could be achieved by editing /etc/fstab file.

---

