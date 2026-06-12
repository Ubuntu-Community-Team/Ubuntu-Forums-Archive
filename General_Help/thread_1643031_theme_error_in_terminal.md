---
title: "theme error in terminal?"
date: 2010-12-11
forum: General Help
---

### Post by princeofnam on 2010-12-11
I get this fairly often and can't exactly decipher what it means.

> sushi@Ragnarork:~$ /home/sushi/.themes/gommapiumalooks/gtk-2.0/gtkrc:234: error: invalid string constant "clearlooks-panelbg", expected valid string constant
/home/sushi/.themes/gommapiumalooks/gtk-2.0/gtkrc:234: error: invalid string constant "clearlooks-panelbg", expected valid string constant


I found through google this solution

> 
[B]Yes, I had this problem. I fixed it by modifying the gtkrc [file]("http://gnome-look.org/content/show.php?content=69913&forumpage=1&PHPSESSID=6#"):

At the very top, there is a line that includes some text like  "\ntooltips_bg_color" and "\ntooltips_fg_color". The problem is that  mail-notification uses the tooltip background color, but not the tooltip  foreground color. So, I changed those [values]("http://gnome-look.org/content/show.php?content=69913&forumpage=1&PHPSESSID=6#") to be light text on a dark background.[/B]


but i don't know what that means in application to

> gtk_color_scheme = "fg_color:#E6E6E6\nbg_color:#555753\nbase_color:#363636\ntext_color:#D3D7CF\nselected_bg_color:#3F403D\nselected_fg_color:#7ECC7A\ntooltips_bg_color:#EDDE5C\ntooltips_fg_color:#000000"

---

