---
title: "Nautilus script problem"
date: 2010-07-08
forum: General Help
---

### Post by theneoindian on 2010-07-08
Hi , 
I am trying to write a nautilus script to open directories as another user .  This is the script i made : 

```

for uri in $NAUTILUS_SCRIPT_SELECTED_URIS; do
gksudo -u jon "gnome-open $uri" &
done

```
When I use this , it asks for the password , and then nothing happens . 
My username is jacsp and user jon was created for some other purposes . 
When I replace the username with jacsp , it works , so i think dis has smthng 2 do with the new user jon . 

The DISPLAY env variable is set for jon and xhost access control is disabled and x applications is runnable by user jon . 
Please help me on this .

---

### Post by gzarkadas on 2010-07-09
Try first to move the double quotes around $uri only, like this:
```

gksudo -u jon gnome-open "$uri" &

```If it still won't work, try to remove the & and, finally, check that user jon has enough permissions to open the supplied uris (for example if they are local directories, they have at least r-x permissions for other users).

---

