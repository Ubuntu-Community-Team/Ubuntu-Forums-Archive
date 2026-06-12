---
title: "compiz - scale plugin only shows one window"
date: 2006-06-08
forum: General Help
---

### Post by jms830 on 2006-06-08
When I activate the scale plugin for compiz, only the window that was in focus stays visible. It just shrinks down, but the other open windows dissapear (until I deactivate it). Anyone know how to fix this?

---

### Post by jocko on 2006-06-08
Have you tried changing the opacity setting for the scale plugin?
In gconf-editor check what setting you have in /apps/compiz/plugins/scale/screen0/options/opacity
(0 is completely transparent, 100 is completely opaque)

---

### Post by jms830 on 2006-06-08
I fixed it, I knew it was going to be something easy like that, I just couldn't find the setting, thanks

---

