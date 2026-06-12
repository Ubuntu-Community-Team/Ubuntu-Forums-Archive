---
title: "New Unity theme?? Don't really know how this happened..."
date: 2011-10-17
forum: General Help
---

### Post by Meelad on 2011-10-17
First when I installed Unity I had only 4 themes available.. However now I have a fifth (pretty nice) one.. (Check attached picture)

I did update my 11.10, but I'm not sure that's how I got this new theme (Adwaita)..

Would somebody update his 11.10 and check?

There could be another reason though.. I messed up a little with Compiz (again), and then restored unity through gnome-shell and not unity 2D.. Could that be how I got this new theme?? Anyway, I just thought to share, because I'm really liking the new theme.. :D

---

### Post by stinkeye on 2011-10-17
Looks like the default gnome-shell theme.
You can change themes within gnome-shell or unity using **gnome-tweak-tool**.

---

### Post by Meelad on 2011-10-17
> **stinkeye said:**
> Looks like the default gnome-shell theme.
You can change themes within gnome-shell or unity using **gnome-tweak-tool**.

I don't have this and I didn't even try to change the theme.. I got it after fixing unity with gnome-shell and logging in with Unity again (I think).

---

### Post by WanderingAlbatross on 2011-10-17
I am still trying to figure out somethings about unity as well.  From your reply, Stinkeye, it seems it is tied in to Gnome somehow, right?  When I upgraded I only got two themes as options, and I don't like either one.  I am using the untiy-2d.  I can't seem to add more.  What is the package to add more themes to unity-2d?

---

### Post by Alwimo on 2011-10-17
Adwaita is added to the list of possible themes when you install Gnome Shell, as it is the default theme of windows in Gnome Shell.
 
Open up your terminal and type "sudo apt-get install gnome-tweak-tool", put in your password and enter "Y" if you're asked whether you want to install it. Once it's installed, you have a program called Advanced Settings or something. Search for Advanced, and open that. Go to the theme page and change the gtk theme and window theme to Ambiance (dark) or Radiance (light) and log out and in again.

---

### Post by stinkeye on 2011-10-18
> **WanderingAlbatross said:**
> I am still trying to figure out somethings about unity as well.  From your reply, Stinkeye, it seems it is tied in to Gnome somehow, right?  When I upgraded I only got two themes as options, and I don't like either one.  I am using the untiy-2d.  I can't seem to add more.  What is the package to add more themes to unity-2d?
The desktop environment in ubuntu 11.10 changed from gnome2 to gnome3.
On gnome you can run various window managers.

Unity 2D uses a slightly tweaked version of the  **Metacity window manager**.
Unity 3d is a plugin for the **compiz window manager**.
GNOME-shell uses the **Mutter window manager**

So they're all desktop shells using different window managers running on gnome.

If you install gnome-tweak-tool it will also install gnome-shell as a dependency and will be added to the session choices
at the login screen.
If you can't run Unity3d you may have problems running gnome-shell as well pal.:P

---

### Post by WanderingAlbatross on 2011-10-18
Thanks for your help, and for Stinkeye as well.  Once I installed the package it made an amazing transformation to the whole system.  I didn't even have to go into the menu for advanced system settings to see it.  Once I went in I saw there are a lot more options now.

---

### Post by WanderingAlbatross on 2011-10-18
I never tried 3D.  I am really not that interested in too many bells and whistles, so wanted to take the low road. :)

---

