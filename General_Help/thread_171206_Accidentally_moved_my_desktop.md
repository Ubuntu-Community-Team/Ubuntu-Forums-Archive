---
title: "Accidentally moved my desktop"
date: 2006-05-06
forum: General Help
---

### Post by blue_thunder on 2006-05-06
This morning I was moving a file with sudo, and I ended up not typing the file name and just leaving off at /Desktop. Things are starting to get weird. I have deleted files sitting on my desktop now, and they won't disappear. I have to search for files that I download to my desktop, and it finds them there, but I don't see them. I tried to move /Desktop back, but things are still weird. Any help would be appreciated. The files I have deleted and are sitting there give me this error: Error "file not found" while deleting...

---

### Post by souki on 2006-05-06
if you didn't logoff that's normal

- logoff first
- then, from a console, move your Desktop back and set owner+permissions on it

---

### Post by phektus on 2007-10-24
This also happened to me. I ran gconf-editor and set the desktop_is_home_dir variable to false. I also did chmod 755 ~/Desktop to set the folder drwxr-xr-x permissions then rebooted. Still, my home folder content is showing in my desktop. Anybody here knows how to fix this?

---

### Post by 23meg on 2007-10-26
[http://ubuntuforums.org/showthread.php?t=581498](http://ubuntuforums.org/showthread.php?t=581498) may help.

---

