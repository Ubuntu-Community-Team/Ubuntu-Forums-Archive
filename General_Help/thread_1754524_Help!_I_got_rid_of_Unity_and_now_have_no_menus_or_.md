---
title: "Help! I got rid of Unity and now have no menus or buttons!"
date: 2011-05-10
forum: General Help
---

### Post by Belscb on 2011-05-10
Hi all,

I've been using Linux for 2 years now, but I'm still only a very basic user of Ubuntu.

I just upgraded to Ubuntu 11.04. I hated the new Unity interface, so I went on preferences and clicked to disable it. Now I don't have *any* menus or buttons to control the system! I don't even know how to re-enable Unity if I wanted to! 

What I'd *really* like to do is figure out a way to get back my classic desktop settings...but right now, I'd be happy just to get Unity back!

Thanks for your help,
Belscb

---

### Post by mcduck on 2011-05-10
If I understood right you just went to Compiz settings and disabled the Unity plugin? That sure would result in what you described, Unity desktop session without Unity. :)

All you need to do is enable it again in CompizConfig Settings Manager (or by adding "unityshell" to the *apps/compiz-1/general/screen0/options/active_plugins* -key in gconf).

What comes to accessing the old desktop instead of Unity, that's something you can select in the login screen. Just click the "Session" button near  the bottom of the login screen after selecting your user and choose Classic Gnome.

---

### Post by Belscb on 2011-05-10
Yes, that's exactly what I did. Unity Desktop session without Unity is pretty much as frustrating as it sounds...lol. My GUI is severely impaired.

How do I do what you've suggested using only hotkeys? Thanks so much for your help!

---

### Post by oliveryty on 2011-05-10
If you did not shut your computer down until now I suggest you press Ctrl + Alt +F1 to enter the text interface. Log in the computer following the instruction of the text. Then enter either of the following commands:

sudo apt-get install unity-2d;

sudo apt-get install kubuntu-desktop;

or, sudo apt-get install xfce4  


either of the above commands, and then press Ctrl + Alt +F7 to return to the graphic interface, 

the log in after choose the desktop session, unity 2d, kubuntu, or xfce.

---

### Post by hawthornso23 on 2011-05-10
> **oliveryty said:**
> If you did not shut your computer down until now I suggest you press Ctrl + Alt +F1 to enter the text interface. Log in the computer following the instruction of the text. Then enter either of the following commands:

sudo apt-get install unity-2d;

sudo apt-get install kubuntu-desktop;

or, sudo apt-get install xfce4  


either of the above commands, and then press Ctrl + Alt +F7 to return to the graphic interface, 

the log in after choose the desktop session, unity 2d, kubuntu, or xfce.

Suggesting he install a different GUI is overkill in my opinion.

Try simply rebooting (use the power switch - inelegant I know but it is quick and brutal and it gets the job done. Then when you type in your username to login, select "ubuntu classic" for the session type. You'll be back in the familiar land of gnome2 and can configure it to your hearts content.

---

### Post by Belscb on 2011-05-10
Thanks you guys! I've now fixed it and returned to Ubuntu Classic. Couldn't have done it without you. :-)

---

