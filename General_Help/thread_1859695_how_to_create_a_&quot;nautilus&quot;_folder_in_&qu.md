---
title: "how to create a &quot;nautilus&quot; folder in &quot;/.config/&quot; ?"
date: 2011-10-14
forum: General Help
---

### Post by b666 on 2011-10-14
just installed 11.10. 

i created two other users/profiles. but when i try to log into them, to set them up, it gives me a warning saying that i need to create a folder: "home/jimbo/.config/nautilus". 

how can i create that? note that when i log into those profiles i cant access things like terminal and whatnot. so how can i create the folders from my own profile? for example, right-click create folder doesn't work.

---

### Post by mcduck on 2011-10-14
How did you create the new users? That directory should be automatically created when needed, just like pretty much any of the setting files & directories in user's home. The error message sounds like there might be some permission issue preventing the directory from being created.

Make sure those new user's home directories belong to the users, and have appropriate read/write permissions.

---

### Post by b666 on 2011-10-14
i created them just after i created my first one, through typing 'users' in the dash box, and so on.. 

anyways, i think everything is ok now. i deleted them and recreated them, and everything works as it should - no warnings. thanks very much for replying, it helped me by making me think that going though things a second time might work :)

---

