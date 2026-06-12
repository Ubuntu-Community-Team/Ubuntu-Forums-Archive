---
title: "Bind a directory for desktop"
date: 2009-10-02
forum: General Help
---

### Post by Lawand on 2009-10-02
I am trying to make my Windows XP installation and my Xubuntu installation share the same desktop, so I edited XP's desktop directory using TweakUI and made it **C:\workspaces\desktop**, now I believe I should bind **/home/lawand/Desktop** (Xubuntu's desktop) to that directory like this:
```
sudo mount --bind /media/XP/workspaces/desktop /home/lawand/Desktop
```
(of course my C:\ partition is mounted at **/media/XP/**)

Now the directory **/home/lawand/Desktop** successfully shows (in the file explorer of Xfce, Thunar) the contents of **C:\workspaces\desktop** but I can't see those files and folders in the actual desktop.

Am I missing something?

---

### Post by Lawand on 2009-10-02
What do you know!, the good old F5 just did the trick :)

---

### Post by sisco311 on 2009-10-02
> **Lawand said:**
> I am trying to make my Windows XP installation and my Xubuntu installation share the same desktop, so I edited XP's desktop directory using TweakUI and made it **C:\workspaces\desktop**, now I believe I should bind **/home/lawand/Desktop** (Xubuntu's desktop) to that directory like this:
```
sudo mount --bind /media/XP/workspaces/desktop /home/lawand/Desktop
```
(of course my C:\ partition is mounted at **/media/XP/**)

Now the directory **/home/lawand/Desktop** successfully shows (in the file explorer of Xfce, Thunar) the contents of **C:\workspaces\desktop** but I can't see those files and folders in the actual desktop.

Am I missing something?

Go To: xfce4 menu(Applications) -> Settings -> Desktop -> Icons tab -> Icon type and select *Files/launcher icons*

EDIT:
D'oh!!! so that's the default option in Xubuntu. :)

---

### Post by Lawand on 2009-10-02
My problem was solved when I refreshed the desktop using F5 :)
Anyway, thanks for your help!

---

### Post by Lawand on 2009-10-02
The question now is, why is it that every time I add or delete or rename something in the desktop, those changes doesn't display unless I press F5? (this behavior doesn't happen in case I un-mounted the desktop back to default...)

---

