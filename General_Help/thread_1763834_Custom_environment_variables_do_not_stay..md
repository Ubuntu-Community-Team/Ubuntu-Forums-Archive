---
title: "Custom environment variables do not stay."
date: 2011-05-20
forum: General Help
---

### Post by smallfryfury on 2011-05-20
I just upgraded to 11.04
When I create environment variables such as:

export FG_SCENERY=/home/justin/.fgfs/scenery:/home/justin/FG_SCENERY

They remain until I close terminal. These custom variables appear under printenv unless I close terminal. Programs act like these variables do not exist if I have closed terminal, but are able to use them if I haven't.

Its just an inconvenience, but any help would be appreciated.

---

### Post by Mr. Shannon on 2011-05-21
As mentiond [[COLOR="Blue"]here[/COLOR]]("https://help.ubuntu.com/community/EnvironmentVariables#Persistent environment variables") you could add the export command to the **~/.profile** file.  If you only want the environment variable when running Flight Gear from a shell then putting the export command in **~/.bashrc** should work as well.

---

### Post by prshah on 2011-05-21
> **smallfryfury said:**
> 
export FG_SCENERY=/home/justin/.fgfs/scenery:/home/justin/FG_SCENERY

They remain until I close terminal. 

As suggested, place in your ~/.bashrc; if you want it available globally (eg, multiple users), place it in your "/etc/environment" file (create if not present).

---

