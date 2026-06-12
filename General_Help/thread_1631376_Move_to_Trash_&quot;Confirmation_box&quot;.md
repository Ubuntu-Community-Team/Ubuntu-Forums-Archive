---
title: "Move to Trash &quot;Confirmation box&quot;"
date: 2010-11-26
forum: General Help
---

### Post by Keypel on 2010-11-26
When I hit the del button, the item in question goes directly to the trash bin without even asking. Does Ubuntu have a Move to Trash "Confirmation dialog box" asking if you really want to send "x" number of item(s) to the trash bin?

---

### Post by karthick87 on 2010-11-26
Press ALT+F2 and type [B]gconf-editor

[/B]Navigate to** /apps/nautilus/preferences/confirm_trash**  and make sure it is checked.

---

### Post by Keypel on 2010-11-26
@karthick87

I did as you said and the setting is/was/still is checked.

---

### Post by karthick87 on 2010-11-26
> **Keypel said:**
> When I hit the del button, the item in question goes directly to the trash bin without even asking. Does Ubuntu have a Move to Trash "Confirmation dialog box" asking if you really want to send "x" number of item(s) to the trash bin?

Are you talking about deleting the file by hitting the delete button or moving to trash by right clicking the file?There is no way to get a delete confirmation on  delete in Ubuntu. This feature has been requested many times in ubuntu, but it is not implemented so far.

---

### Post by Keypel on 2010-11-26
By hitting the del button... I guess the feature does not exist as you say.

It's just that I'm afraid of hitting the del button without knowing it and later emptying the the trash bin with the notion that everything in the trash was meant to be in the trash.

I guess a real life analogy would be setting your wedding ring on the desk and then bumping it into the trash with your elbow. Later you take out the trash without knowing your wedding ring was in it. I'm sure a real life dialog box asking "Are you sure you want to send your wedding ring to the Trash Bin?" would be helpful lol

It's standard on MicoSh#t Winblows, I'm surprised Ubuntu doesn't have a counter part.

---

### Post by wojox on 2010-11-26
> **Keypel said:**
> Does Ubuntu have a Move to Trash "Confirmation dialog box" asking if you really want to send "x" number of item(s) to the trash bin?

Only if you right click. By the way, never take your ring off. :D

---

### Post by WorMzy on 2010-11-26
Keeping up with the analogy, make copies of your ring as backups. Just in case.

---

### Post by Keypel on 2010-11-26
> **WorMzy said:**
> Keeping up with the analogy, make copies of your ring as backups. Just in case.

:lolflag::lolflag::lolflag::lolflag::lolflag:

---

### Post by aysiu on 2010-11-26
Ubuntu's is just a different approach. Unfortunately, you prefer the Mac OS X approach, and you're using Ubuntu. So you have the choice of using Mac OS X... or just getting used to the way Ubuntu does things until the Gnome devs decide to implement things another way.

You can have Ubuntu prompt you when you empty the trash, just not when you move things to the trash. That's all you get.

Make regular backups of all your files, and look at what's in your trash before you empty it. That's the best you can do right now. At least they finally implemented restoring trashed items to their original locations.

---

### Post by WorMzy on 2010-11-26
Also, note that there are other desktop environments than GNOME (Ubuntu). There's KDE, XFCE, LXDE, and plenty of others. If GNOME isn't meeting your requirements, then feel free to try one of the others. Perhaps it will provide the features that you feel are lacking from the GNOME environment.

GNOME and KDE are the two "major" players on the DE scene, but XFCE and LXDE are pretty popular too.

You can install KDE by installing kubuntu-desktop, and likewise, you can install XFCE by installing xubuntu-desktop. LXDE is a fairly new addition to the Ubuntu ranks, install it by installing lubuntu-desktop. If you install one of these other Desktop environments you may need to choose which one you want to use from the login screen.

---

### Post by karthick87 on 2010-11-27
+1 on post 10.

---

