---
title: "Windows unable to resize to show all contents"
date: 2011-10-25
forum: General Help
---

### Post by supershin on 2011-10-25
In Lucid Lynx on a laptop, 1366*768, with the default theme I'm unable to properly view certain windows, for example, disk utility. The window comes up but I can't view all the text in it. 

Tried full-screen and resizing but it doesn't work. The bottom part of the window which has mount and format is where I can "see" up to. I am fully up-to-date. Any ideas on a fix?

---

### Post by dcstar on 2011-10-26
> **supershin said:**
> In Lucid Lynx on a laptop, 1366*768, with the default theme I'm unable to properly view certain windows, for example, disk utility. The window comes up but I can't view all the text in it. 

Tried full-screen and resizing but it doesn't work. The bottom part of the window which has mount and format is where I can "see" up to. I am fully up-to-date. Any ideas on a fix?

You can try reducing the Font DPI resolution value in System-Preferences-Appearence-Fonts-Details.

---

### Post by supershin on 2011-10-28
Thanks, I realized I had changed the font from the defaults so I'm gonna change to back and see if that works. 

To reset font settings: 
In terminal:
gconftool-2 --unset /desktop/gnome/interface/font_name
gconftool-2 --unset /desktop/gnome/interface/document_font_name
gconftool-2 --unset /desktop/gnome/interface/monospace_font_name
gconftool-2 --unset /apps/metacity/general/titlebar_font
gconftool-2 --unset /apps/nautilus/preferences/desktop_font 

[http://askubuntu.com/questions/4989/reset-gnome-font-configuration]("http://askubuntu.com/questions/4989/reset-gnome-font-configuration")

It worked for me.

---

