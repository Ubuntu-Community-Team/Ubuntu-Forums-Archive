---
title: "XF86Config"
date: 2006-02-26
forum: General Help
---

### Post by Kiwinote on 2006-02-26
Hello,

-To get tv-out working on my graphics-card I need to find: 'your "XF86Config" file (usually located in "/etc/X11/")'
-and add this line: 'Option "TV" "yes"'
-The problem is I can't locate this file, any ideas as to the location?

Thanks,
Kiwinote

---

### Post by bosonflux on 2006-02-26
I believe in Ubuntu it's /etc/X11/xorg.conf.

---

### Post by Kiwinote on 2006-02-26
Thanks, by the looks of it, it is in that file. When I read it as a normal user I can read the text, but as soon as I open it as root user using sudo gedit /etc/X11/xorg.conf ,so that I can edit it I get a empty file. How can I edit this file?

Kiwinote

---

### Post by Kiwinote on 2006-02-26
Problem solved.

---

