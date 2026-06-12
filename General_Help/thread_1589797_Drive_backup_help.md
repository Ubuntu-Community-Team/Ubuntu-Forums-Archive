---
title: "Drive backup help"
date: 2010-10-06
forum: General Help
---

### Post by hackling on 2010-10-06
Hi guys this is my first post here so bare with me. If its in the wrong spot sorry and feel free to move it:P.
 
I have 2 sets of identicle drives.
 
2 1.5 tbs used for video
and
2 1.0 tbs used for files
 
all 4 have and need ntfs filesystem
 
I have one out of each set shared on my network using samba so I can access them remotly. What I would like to do is every night at around 3 am is backup each drive to the second one. So the 1.5 to the 1.5 and the 1.0 to the 1.0, all the second drive is going to be is a backup.
 
I realy dont want to do RAID or fakeRAID I just want a simple backup at the same time every night.
 
Im running ubuntu server 10.04.1 64bit and am comfertable using the terminal I do have gnome instlled so anything with a GUI is also possible. 
 
Thank you for any help

---

### Post by Dex73 on 2010-10-07
I'm not sure but there is probably a way to make an application run on some sort of timer.

For the back up it's self, have you looked into luckybackup yet? It even has ssh and remote module built right in. You just need to go to modify and then advanced. Plus you can set any directory you want to back up any where you want. Then you can save that backup setup and do it again when ever you want. (rsynce is the backend for lucky)

Sorry I don't have a solution for need for an automated timer.

---

### Post by hackling on 2010-10-07
Thanks for the idea I have found several programs like this but its still nice to get recommendations o and sorry for the spelling.  Im amazed at how hard it is to find something like this you think it would be common on a server but I guess RAID solves that for most users lol.

---

### Post by Locke_99GS on 2010-10-07
If I may ask, why do you not want RAID? It seems like it would exactly solve your problem, removing the need to perform any nightly copy.

---

### Post by hackling on 2010-10-07
The main reason I dont want RAID is i dual boot between windows server 2008 and ubuntu and I dont feel like messing around to get them both to work.

---

### Post by Dex73 on 2010-10-15
I ran across this in ubuntu software center. I haven't used it myself, but it maybe something you could use.

---

