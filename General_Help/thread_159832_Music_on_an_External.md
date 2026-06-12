---
title: "Music on an External"
date: 2006-04-13
forum: General Help
---

### Post by mcletter on 2006-04-13
Hi, I was just curious if it was possible, using RhythmBox, or any other music program, to import music from a folder on an external harddrive that is networked from a windows computer. I can acess the folder but cant acess it from the music program. Any help would be awesome. thanks :)

---

### Post by ncappel1 on 2006-04-14
Not sure if this would work, but if you put a shortcut to the folder in your main music folder, (the one that it reads from normally), it might look into the shortcut and pull the music out of there. This way you wouldn't have to use extra hard drive space to have double copies of all your music files. 

I've never tried it though, so I can't say confirm if it will work.

---

### Post by mcletter on 2006-04-14
I solved my problem, what I ended up doing was changing the share name of the external on the windows computer to just "external", so I could just use //jeff/external.. It works great now. :)

---

### Post by Face1 on 2006-04-15
Also, a smb share (a windows share) can be mounted on your filesystem, just like another HD partition using the mount command.  If you did that, then rhythmbox would just see it as another directory.

---

