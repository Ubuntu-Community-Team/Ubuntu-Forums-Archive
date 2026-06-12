---
title: "how to uninstall these programs??"
date: 2009-10-12
forum: General Help
---

### Post by Amgad elsaiegh on 2009-10-12
i dowonloaded a file-sharing program called frostwire on Ubuntu 9.10 as a .deb file ,installed it but it didn't work :confused:
now i need to uninstall it ,i couldn't find it add/remove applications OR  synaptic package manager ,so what should i do !!!

---

### Post by azmo35 on 2009-10-12
To uninstall a .deb file, deselect it in your package manager, or type:

    sudo dpkg -r package_name

---

### Post by mcduck on 2009-10-12
It *will* show up in Synaptic, so if you didn't find it there you didn't do a proper search.

Anyway, "sudo apt-get remove *packagename*" will work just as well.

(Add/Remove isn't even supposed to list any extra stuff, or even all the stuff in the repositories. It's not a full-blown package management tool but just a simple tool for installing and removing a small selection of most popular applications)

---

### Post by Amgad elsaiegh on 2009-10-12
problem solved 
Thanks :)

---

