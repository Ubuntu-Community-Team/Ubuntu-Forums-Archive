---
title: "bash script to edit gconf settings"
date: 2011-07-08
forum: General Help
---

### Post by aquabanianskakid on 2011-07-08
If you know how to change gconf settings from the command line or bash script I could use some help.

I've been trying to write a bash script that will change the gconf settings for docky. The goal is to make it have a setup similar to Elementary OS or Pinguy OS... that means one docky instance on the bottom and one on the left. I just can't seem to get the commands working right at all. This is one setting I have been trying to change but every time I get an error about primitive types.

gconftool --type List --set /schemas/apps/panel/general/toplevel_id_list [top_panel]

Any clue?

---

### Post by dino99 on 2011-07-08
sudo gconf-editor

---

### Post by aquabanianskakid on 2011-07-08
Maybe you misunderstood me or didn't read my post, but I am trying to do this from the command line or a bash script.

---

### Post by mc4man on 2011-07-08
You don't need to use root for user setting - don't have docky but use something like this 

```
gconftool-2 -s --type=list --list-type=string /schemas/apps/panel/general/toplevel_id_list [top_panel]

```

---

### Post by aquabanianskakid on 2011-07-08
It looks like that just might be what the doctor ordered! Thanks a bunch for the help. I should be able to get the script running now.

---

