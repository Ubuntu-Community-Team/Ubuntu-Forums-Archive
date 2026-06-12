---
title: "Nautilus icons have become bigger"
date: 2012-05-28
forum: General Help
---

### Post by ashhab2010 on 2012-05-28
I had installed Mac4Linux from [http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac]("http://www.howtoforge.com/mac4lin_make_linux_look_like_a_mac")
I didnt like it that much so i removed it.  
After removing it my nautilus toolbar icons have become large  
  
[IMG]http://i.stack.imgur.com/qfCS8.png[/IMG]
  
Previously it used to look like this with small icons 
[IMG]http://i.stack.imgur.com/MwsPY.png[/IMG]  
  
How do i revert it back?

---

### Post by mc4man on 2012-05-28
To fill this thread in - you got the answer here
[http://askubuntu.com/questions/136085/nautilus-toolbar-icons-became-bigger](http://askubuntu.com/questions/136085/nautilus-toolbar-icons-became-bigger)

In a nutshell - the setting is available in either dconf (org.gnome.desktop.interface toolbar-style) or gconf (/desktop/gnome/interface/toolbar_style) depending on Ubuntu release

In both cases there are 4 available options, the default is both-horiz
The 4 are - "both", "both-horiz", "icons", and "text".

I use icons here because it's cleaner & I know what the icons mean

---

### Post by ashhab2010 on 2012-05-29
> **mc4man said:**
> To fill this thread in - you got the answer here
[http://askubuntu.com/questions/136085/nautilus-toolbar-icons-became-bigger](http://askubuntu.com/questions/136085/nautilus-toolbar-icons-became-bigger)

In a nutshell - the setting is available in either dconf (org.gnome.desktop.interface toolbar-style) or gconf (/desktop/gnome/interface/toolbar_style) depending on Ubuntu release

In both cases there are 4 available options, the default is both-horiz
The 4 are - "both", "both-horiz", "icons", and "text".

I use icons here because it's cleaner & I know what the icons mean

Thanks!!!!!!:D

---

