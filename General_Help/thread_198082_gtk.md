---
title: "gtk"
date: 2006-06-16
forum: General Help
---

### Post by maniacmusician on 2006-06-16
how do you install gtk themes in xubuntu? I know there was a preferences option in gnome, but i can't find it in xcfe..

---

### Post by ayoli on 2006-06-16
i don't know if install themes under ~/.themes works on xfce, but you can insll themes in /usr/share/themes

edit: then you can use it by creating/editing ~/.gtkrc-2.0 and put this line in it:

include "/usr/share/themes/your_theme/gtk-2.0/gtkrc"

or use gtk-theme-switch (which is in repositories) if you want a graphical way to change gtk theme

---

### Post by maniacmusician on 2006-06-16
Hey; thanks a lot for your suggestions. It was too much of a pain to to use the manual method and gtk-theme-switch wasn't too appealing, but no worries. I found the option  in Xubuntu. For anyone else that's looking for it:

|Applications>Settings>User Interface Settings. 

it's nice and smooth, too. But while we're on the topic of themes, one more question: I recently installed xffm for its network browser, which works pretty well...but everytime I use it, it totally changes my desktop and uses the xffm file manager consistently. to remove it, i have to go to xfce task manager, and kill xffm-deskview. is there any way i can get it to just open its file manager and nothing else? 

thanks

---

### Post by ayoli on 2006-06-17
you should have an option to run xffm without deskview, try type in term :

xffm --help 

find the option, and make a launcher to run easily xffm with suitable options for you

---

