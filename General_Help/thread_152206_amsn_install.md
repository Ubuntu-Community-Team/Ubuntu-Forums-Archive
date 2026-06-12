---
title: "amsn install"
date: 2006-03-29
forum: General Help
---

### Post by yatesDELTA on 2006-03-29
i have downloaded amsn but how do i install it. I assume it is via terminal but i need the command line. thanx, yatesDELTA

---

### Post by encompass on 2006-03-29
not sure if it works in kubuntu but have you looked at automatix?  search in the forums... worked for me in ubuntu.

---

### Post by gingermark on 2006-03-29
[QUOTE=yatesDELTA]i have downloaded amsn but how do i install it. I assume it is via terminal but i need the command line. thanx, yatesDELTA[/QUOTE]
If you downloaded a .deb file then type "sudo dpkg -i packagename.deb"

Otherwise, amsn is available in the universe repository. Enable the universe repository (if you haven't done already), and install with adept or type "sudo apt-get install amsn".

To enable the Universe repository type "kdesu kate /etc/apt/sources.list" and remove the '#' symbols in front of the universe lines. Save the file, then type "sudo apt-get update" and proceed as above.

---

