---
title: "Permission problem - 11.10"
date: 2012-04-04
forum: General Help
---

### Post by Onoku on 2012-04-04
I downloaded some icon sets and tried to move them to the icons folder but i am getting this error...

>  cannot be copied because you do not have permissions to create it in the destination.                                 

This seems like there should be an easy fix to this, but I'm not the most competent Ubuntu user.

---

### Post by Gremlinzzz on 2012-04-05
> **Onoku said:**
> I downloaded some icon sets and tried to move them to the icons folder but i am getting this error...

                             

This seems like there should be an easy fix to this, but I'm not the most competent Ubuntu user.

gksu nautilus

in terminal gives you permission to do anything:popcorn:

---

### Post by tlan on 2012-04-05
> **Onoku said:**
> I downloaded some icon sets and tried to move them to the icons folder but i am getting this error...

                             

This seems like there should be an easy fix to this, but I'm not the most competent Ubuntu user.

open a terminal and type sudo nautilus and hit enter, this will open your file manager with root permissions, open a second window and copy and paste the files.

---

### Post by Onoku on 2012-04-05
> **tlan said:**
> open a terminal and type sudo nautilus and hit enter, this will open your file manager with root permissions, open a second window and copy and paste the files.

okay so as long as the terminal is open when i sudo nautilus, I will have folder permissions? thanks

---

