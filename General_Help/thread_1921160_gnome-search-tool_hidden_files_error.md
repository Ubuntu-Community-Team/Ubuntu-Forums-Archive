---
title: "gnome-search-tool hidden files error"
date: 2012-02-06
forum: General Help
---

### Post by beaucoder on 2012-02-06
Hi All,

gnome-search-tool won't find hidden files from Home - User with option set to "show hidden files", 

but will find them in starting at the right hidden folder, i.e., '.local' which is under Home - User as Home/User/.local/...

This should not happen.

How to fix? Make it work somehow? Use a different search pkg?

The file name was to contain 'note' and the "show hidden files" option was added.

Thanks,

Ken Wagner

---

### Post by oklokl on 2012-02-06
[COLOR=#0900FF][COLOR=#000000][FONT=Lucida Grande]gnome-control-center
+

add
user [/FONT][/COLOR][/COLOR]Add Panel

[COLOR=#0900FF][COLOR=#000000][FONT=Lucida Grande]gksu gnome-search-tool

[/FONT][/COLOR][/COLOR]Change

[COLOR=#0900FF][COLOR=#000000][FONT=Lucida Grande]gnome-search-tool
setting
+ hidden view add[/FONT][/COLOR][/COLOR]

---

### Post by beaucoder on 2012-02-06
Hi [oklokl]("http://ubuntuforums.org/member.php?u=1264373"),

I am on Ubuntu 11.10. I have tried the "Add" setting in the search tool. Even the correct "User" settings. With and without 'gksu' prefix in the terminal. 

Still no success when starting from Home/User. But starting at the sub-folder ".local" (Home/User/.local) _does_ work for this is where the file sought is in another sub-folder 3 levels down. 

Makes no sense.  (Or am I missing something obvious here??)

Ken

---

### Post by oklokl on 2012-02-06
Sorry
 I do not know the cause.
 I'm sorry not to help.

---

