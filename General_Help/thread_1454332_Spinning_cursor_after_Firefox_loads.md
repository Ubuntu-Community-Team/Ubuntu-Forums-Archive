---
title: "Spinning cursor after Firefox loads"
date: 2010-04-14
forum: General Help
---

### Post by mfox on 2010-04-14
What I have noticed on several versions of Ubuntu, both 32 and 64 bit (including 9.10, 10.04 b2 and UNR 9.10) is that after the launch of Firefox (including the current 3.6.3 version), I continue to get a spinning cursor for more than 10 seconds after the FF window is present and ready to accept input.  Sometimes I get it only when moving the cursor outside the FF window and other times it will be in the window, too.  I have even noticed it persist for a short time after quitting FF.  I think it's definitely related to FF because I don't see this occur unless FF is launched, not even when another browser (Chromium in this case) is launched. To add to the mystery, I see it in Ubuntu and Mint 8 xfce, but not in Ubuntu-based distros with simpler window managers like Mint 8 fluxbox or CrunchBang 9.04 (openbox).  To try to get rid of this, I have tried various FF configuration speedups available from the Net - changes implemented through about:config.  These do speed up FF, but they don't get rid of the spinning wheel.

As far as I can tell, the spinning wheel has no impact on FF operation - it doesn't stop me from entering a url and accessing it, though perhaps it slows down implementation.  It's just annoying and I'd like to get rid of it if possible.  Any ideas what this is and how to fix it?

---

### Post by lovinglinux on 2010-04-15
It's probably some bug in Gnome notification system.

You could try  to drag the Firefox launcher to your desktop, then browse it with nautilus and find firefox.desktop file. Open it with a text editor and set StartupNotify to false. This stops Firefox spinning icon on KDE.

---

### Post by mfox on 2010-04-15
Thanks, lovinglinux; this looks useful, but could you explain in more detail how I implement the first part.  I found a firefox and firefox-3.5.8 executable files in /usr/lib.  Is this what you mean by the launcher?  When I drag either to the desktop and try to open them with either the file browser (Nautilus I presume), or gedit, I get an error.

---

### Post by lovinglinux on 2010-04-15
No. Is not the executables. 

Open "Applications >>> Internet" menu from your panel, just like if you would  start Firefox, but instead of clicking the Firefox icon, drag it to your desktop. This will create a shortcut to Firefox in your Desktop. Then launch the file browser (nautilus) and go to your Desktop in the folder tree. You should see the new shortcut to Firefox there. Right-click on it an select open with "gedit" so you can edit it. Then set the line StartupNotify to false and save it.

---

### Post by mfox on 2010-04-15
Thanks, lovinglinux; this worked and now I have a solution to the mystery of the spinning cursor.  Makes me like Firefox a whole lot more, but is there a way I can make this change permanent without having to have the FF icon on my desktop?  In other words, can I edit the actual file and get rid of the shortcut/alias?

---

### Post by lovinglinux on 2010-04-15
> **mfox said:**
> Thanks, lovinglinux; this worked and now I have a solution to the mystery of the spinning cursor.  Makes me like Firefox a whole lot more, but is there a way I can make this change permanent without having to have the FF icon on my desktop?  In other words, can I edit the actual file and get rid of the shortcut/alias?

Drag the icon from the desktop to your panel.

I wouldn't worry about this. At some point this should go away with new updates.

---

### Post by mfox on 2010-04-15
Maybe, but it could be a long time, as it has been around since at least 8.10.

---

### Post by lovinglinux on 2010-04-15
> **mfox said:**
> Maybe, but it could be a long time, as it has been around since at least 8.10.

Well, I use KDE, which allows to disable the busy cursor ;)

---

### Post by COKEDUDE on 2010-06-06
> **lovinglinux said:**
> Well, I use KDE, which allows to disable the busy cursor ;)

Could you explain how to do that please?

---

### Post by dtfinch on 2010-06-06
What I did on mine (Gnome) was copy the DMZ-White folder from /usr/share/icons to the .icons folder in my home directory, rename it to DMZ-WhiteFixed, and in the cursors subdirectory, replaced "watch" and "left_ptr_watch" with copies of "arrow", then went to system/preferences/appearance/theme/customize/pointer and selected DMZ-WhiteFixed.

It's better to have no busy cursor at all than to have one that's wrong 90% of the time and has a shape that makes it hard to aim.

---

### Post by lovinglinux on 2010-06-08
Looks like this problem will be fixed on Firefox 3.6.4.

---

