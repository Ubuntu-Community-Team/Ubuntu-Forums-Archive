---
title: "resolution not showing in options"
date: 2006-04-20
forum: General Help
---

### Post by rocarm on 2006-04-20
I accidently hit the enter key during install instead of the space to select the resolution i'd like to have on ubuntu. Now i'm stuck on 1024x768. its big and ugly. 

how can i add the 1280x1024 option to the list? I'm sure there's an option somewhere or a file i have to edit? Can anyone help?

---

### Post by krusbjorn on 2006-04-20
You can manually edit /etc/X11/xorg.conf, but it's probably easier to do "sudo dpkg-reconfigure xserver-xorg".

---

### Post by rocarm on 2006-04-20
thanks, that did the trick!

---

