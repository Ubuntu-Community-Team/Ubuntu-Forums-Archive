---
title: "Help Please Need Some Ubuntu Support!!!!!"
date: 2011-03-06
forum: General Help
---

### Post by theunit8 on 2011-03-06
Hi everyone, first of all I'm new to Ubuntu forums and I must say before I signed up for this forum, I was finding a lot of cool stuff directing me straight to these forums. So you are all definitely doing a great job!
Second of all, I'm having some trouble here. Well, when I click my Panel-Places-Home Folder, my home folder does not open. My Audacious opens, and starts playing my music. That is the folder my music is saved to, but I don't recall it ever doing this before? So I'm a little confused. If anyone could let me know how I can fix this so when I click my Home Folder my Home Folder will come up! Not Audacious! Please help, thank you very much.

---

### Post by Krytarik on 2011-03-06
Hi and welcome to the forums!

It seems like you have inadvertedly chosen Audacious as default app to handle folders.

Solution: Open the file "~/.local/share/applications/mimeapps.list" and lookup the entry for "inode/directory", it should be like this:
```
inode/directory=nautilus-folder-handler.desktop;
```Here is a good explanation of what may have caused it:
[http://ubuntuforums.org/showthread.php?t=1675491](http://ubuntuforums.org/showthread.php?t=1675491)

Greetings.

---

