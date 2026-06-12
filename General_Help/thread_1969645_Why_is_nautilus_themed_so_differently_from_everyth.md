---
title: "Why is nautilus themed so differently from everything else?"
date: 2012-04-30
forum: General Help
---

### Post by josephellengar on 2012-04-30
Hello. I'm using 12.04 and Gnome Fallback, and upon upgrade nautilus suddenly decided that it wanted to be themed differently from everything else in the system. I use the radiance theme and the Aw0ken icon set and typically use gnome-tweak-tools to make sure that everything is consistent. Nautilus, however, does not respect either the theme or the icons. You can see a comparison in the screenshot that I put below. The icons in nautilus are the gnome default, while in all of my other applications they are monochrome. Nautilus has that ugly black bar along the top while in every other application I have eliminated the color black, etc. Any idea why this might be or how I can fix it? I couldn't find a key in gsettings or gconf-editor.

---

### Post by Vaphell on 2012-04-30
Have you tried to set everything up again (choose theme and icon set) after the upgrade?
does the new user account experience the same thing? If not then maybe wiping gnome related dotfiles would make nautilus follow settings.

afaik gconf-editor is on the way out and is replaced by dconf-editor.

---

### Post by josephellengar on 2012-04-30
> **Vaphell said:**
> Have you tried to set everything up again (choose theme and icon set) after the upgrade?
does the new user account experience the same thing? If not then maybe wiping gnome related dotfiles would make nautilus follow settings.

 
Already tried both.
 
 
>  
afaik gconf-editor is on the way out and is replaced by dconf-editor.
 
It is, but many programs still use it.
 
Thank you though!

---

### Post by josephellengar on 2012-05-02
Fixed it. I had to delete ~/.config/monitors.xml. No idea why.

---

