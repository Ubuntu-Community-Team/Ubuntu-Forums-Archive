---
title: "Help!!!!!"
date: 2011-01-12
forum: General Help
---

### Post by dreamer10001 on 2011-01-12
some how my root folder was moved to usrs/share/wallpapers and i dont know how to move it back can someone help

---

### Post by lisati on 2011-01-12
And your system is working? :(

Just to clarify, by "root", are you referring to "/"? 

Has stuff that you'd normally expect in your wallpaper folder turned up there by accident?

---

### Post by dreamer10001 on 2011-01-12
yes i mean "/" and its only that and wall papers there and users work find just cant do admin tasks

---

### Post by LetsMugSanta on 2011-01-12
Was anything changed before this happened? ie anything installed or uninstalled, hardware or software, any terminal codes you put in?

---

### Post by dreamer10001 on 2011-01-12
yes i was trying to move a picture there in terminal but i never asked 
it to move the root folder i used sudo mv ~ /abc.jpg/ usr/share/background

---

### Post by LetsMugSanta on 2011-01-12
open up two instances of nautilus. (gksu nautilus is the code). try and see if you can move out the root folder and switch it

---

### Post by dreamer10001 on 2011-01-12
can you explain a little better?

---

### Post by LetsMugSanta on 2011-01-12
> **dreamer10001 said:**
> some how my root folder was moved to usrs/share/wallpapers and i dont know how to move it back can someone help

open up the two instances, copy the root folder or all folders within the root folder that is in the wallpapers folder and move it to what is now / and then switch whatever is at / with the root folder.

I'm not really sure if that will work or not, just trying to eliminate the easiest.

---

### Post by dreamer10001 on 2011-01-13
omg ty i used the gksu nautilus command it allowed me to get administrator privileges and i move the root folder back into the file system thx man really ty

---

### Post by LetsMugSanta on 2011-01-13
Your welcome. Go to the top of the thread now and mark as solved.

---

