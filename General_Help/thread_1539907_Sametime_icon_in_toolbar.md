---
title: "Sametime icon in toolbar"
date: 2010-07-27
forum: General Help
---

### Post by bacardiandwatermelon on 2010-07-27
Hi Guys, just installed lotus notes 8.5.1 and sametime etc.. Everything is working perfectly but was just wondering if there was a way to remove the sametime icon from the tool bar or at least where the file might be located so I can change it so it fits in with my dark theme.. I found heaps of icons under ~/lotus/notes/data/domino/icons but can't seam to find the right one... Cheers

---

### Post by hhh on 2010-07-27
I don't have Sametime, but try this... as root, go to /usr/share/applications and find the Sametime icon. Right-click it and rename it to Sametime_backup (or whatever-it's-called_backup. Actually, copy the file to a different location first, then rename the one in applications so you have 2 backups. I once renamed an icon in applications and it disappeared. You can delete one backup later if you care to). Now open the original file with a text editor and find the line that says "Icon=". It probably says "Icon=Sametime", but whatever. Change it to the path for the icon you want to use (eg. Icon=/usr/share/icons/gnome/24x24/actions/call-start.png).

You may need to logout and in to see the change. This might now work for every instance of the icon (like in the "Open with" menu in Nautilus) but it should show in your main menu and on your taskbar.

HTH, let me know if it worked for you.

---

