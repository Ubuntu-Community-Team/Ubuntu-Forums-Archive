---
title: "Confirm file deletion?"
date: 2011-08-29
forum: General Help
---

### Post by aSystemOverload on 2011-08-29
Ok, how do I activate confirm on delete?

---

### Post by jerrrys on 2011-08-29
in nautilus>edit>preferences

[ATTACH]201052[/ATTACH]

---

### Post by aSystemOverload on 2011-08-29
I have both options ticked.  Let me rephrase.  When I select a file and hit [DEL], I want confirmation before the file is sent to the recycle bin?

---

### Post by jerrrys on 2011-08-29
ok, understand now and the answer is no such option.  when you delete trash it will want a confirm, but thats it.

---

### Post by WyleECoyote on 2011-08-29
you may not want to do this, but... gonna put it out there anyway just in case someone likes it:

open gconf-editor

navigate to /desktop/gnome/interface

select can_change_accels

open nautilus and change the delete command by hitting del key or any key you want for that matter

[IMG]http://img.photobucket.com/albums/v316/checker/Screenshot-kerrey-FileBrowser.png[/IMG]

if you hit delete it will ask if you want to PERMANENTLY delete it so be careful if that is not what you want, I on the other hand do because I never have a problem accidentally deleting something and really wish I could get rid of that stupid trash bin

and don&#8217;t forget to uncheck the change accels otherwise you may accidentally change something you want

---

### Post by aSystemOverload on 2011-08-30
> **jerrrys said:**
> ok, understand now and the answer is no such option.  when you delete trash it will want a confirm, but thats it.


Is this specific to Ubuntu or a general Linux thing?

---

### Post by aSystemOverload on 2011-08-30
I'm a strange one, hybrid if you like.  I typically prefer GUI, but inside the GUI I prefer keyboard.  I don't like having to move the mouse to go into menus, prefer short cuts.

---

