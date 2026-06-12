---
title: "How can I change folder's icon?"
date: 2010-08-29
forum: General Help
---

### Post by MIH1406 on 2010-08-29
Hi,

I have a folder in my Home folder and called "Projects". I want to change the icon of the folder Project so the icon changed in everywhere. In "Places", Open Dialogs, Save Dialogs and Normal View in Nautilus.

What I have done:
Change the icon using Right-Click -> Properties -> Basic Tab -> Clicked the current icon and changed it. But this changed it only in Nautilus. If I added this folder to "Places" it will appear with the Default icon. The same thing if I browsed to it using Open Dialogs or Save Dialogs.

Thanks in advanced,
MIH1406

---

### Post by fragos on 2010-08-29
Perhaps the icon you selected doesn't have an icon for the smaller size used in places. Look in /usr/share/icons and there will be folders for the icon sets you have installed. Find the set you're using and open the folder. Here you'll find folders by use, example Places. Open that and there will be folders labeled by size. The next level is where the actual icons of that size are stored.

---

### Post by MIH1406 on 2010-08-29
I used the same icon for Download folder which works fine for the system Download folder but not for my "Project" folder! I used the icon in the folder Scalable and also tried the other sizes.

---

### Post by MIH1406 on 2010-09-01
Up Up Up

---

### Post by hellblazer on 2010-09-30
I'm looking to change the folder icon everywhere on my system, but I can't even find it in under /usr/share/icons!

---

### Post by fragos on 2010-09-30
You didn't dig deep enough. Within /usr/share/icons first select the folder for your icon set, example Humanity. Then select Places and you'll find the folder icons for Humanity.

---

