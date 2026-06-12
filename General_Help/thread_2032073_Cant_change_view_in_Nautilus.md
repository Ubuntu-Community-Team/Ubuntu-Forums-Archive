---
title: "Cant change view in Nautilus"
date: 2012-07-23
forum: General Help
---

### Post by OlJoe on 2012-07-23
ubuntu 12.04

when I click on any menu items (file, edit etc) in Nautilus they will not open so I cant change from icon view to list. I can change use the control+2 but i want to change the default view.  sudo Nautilus allowed me to change the view however it didnt stick.
Idea's? I dont know Linux so use small words..:confused:

---

### Post by dino99 on 2012-07-23
goto Applications -> System Tools -> dconf 

select:

org->gnome->nautilus->preferences->default-folder-viewer

---

### Post by OlJoe on 2012-07-23
> **dino99 said:**
> goto Applications -> System Tools -> dconf 

select:

org->gnome->nautilus->preferences->default-folder-viewer

Where do I find Applications? 

thanks

---

### Post by OlJoe on 2012-07-23
OK got it thanks. I had to install dconf editor then pretty simple. I never did find the "Applications" tho

---

