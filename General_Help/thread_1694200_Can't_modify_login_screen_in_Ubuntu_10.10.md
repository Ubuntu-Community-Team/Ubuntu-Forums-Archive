---
title: "Can't modify login screen in Ubuntu 10.10"
date: 2011-02-24
forum: General Help
---

### Post by xXDarkRoninXx on 2011-02-24
The first time I installed Ubuntu onto my computer, I downloaded all of the major appearance applications like Tweak. Using Tweak, I modified the login screen to have a custom wallpaper and no sound to play when I login, and it worked perfectly. When I re-installed Ubuntu after that first time (I re-installed it because I totally screwed with the GUI) and every time after that, I go to use Tweak and it still allows me the option to modify the login screen. However, after I make the modifications and restart the GUI, the login screen background is just a blank purple wallpaper and the login sound still plays when I login (both are things I didn't select). I open up Tweak and the modifications I made are still there, but they don't apply. What's up?

---

### Post by An Sanct on 2011-02-24
The login screen is manager has changed for Maverick Meerkat, [Ubuntu Tweak]("http://ubuntu-tweak.com/") can change the background and sound playing.

---

### Post by zzzzaxxxx on 2011-02-24
Hi,

I have the same problem: I set the login wallpaper via Ubuntu Tweak (which also shows the new wallpaper), however, when I restart I get this purple colored background.

---

### Post by An Sanct on 2011-02-24
It works for me (Ubuntu 10.10 Maverick Meerkat 64bit).

---

### Post by Jouke74 on 2011-02-24
> **zzzzaxxxx said:**
> Hi,

I have the same problem: I set the login wallpaper via Ubuntu Tweak (which also shows the new wallpaper), however, when I restart I get this purple colored background.

This is a nasty one to find out:
You need to give read permissions for the background file to all users, since technically you are not the logged in user yet when you are at the login screen. So of you want X.jpg to be your background at login, you need to give read permissions to Owner, Group and Others. When you copy a picture file from your USB stick usually Owner permissions are given, but no other permissions.

---

### Post by xXDarkRoninXx on 2011-02-24
Hey thanks for the replies, I finally solved the problem.

For the wallpaper, I was trying to use a file that was not in the /~/usr/share/background folder (and I guess that doesn't work). I followed the instructions from the following link: [http://www.youtube.com/watch?v=jLD-N3BZRtI](http://www.youtube.com/watch?v=jLD-N3BZRtI) (it's still inconvenient to have to transfer the files whenever I want to change the background, but no big deal)

For the login sound, I was trying to disable it through Tweak, when the best way to do it is to go to System->Preferences->Startup Applications and un-check the GNOME Login Sound. ([http://tech.mobiletod.com/how-to-disable-or-change-login-sound-in-ubuntu-10-10/](http://tech.mobiletod.com/how-to-disable-or-change-login-sound-in-ubuntu-10-10/))

If you found any better solutions please post them.

---

### Post by vos on 2011-03-07
There is a reall simple and easy way I found a while back which uses the Appearance app to make all the changes directly in GDM.

To change the theme add gnome-appearance-properties to GDM's autostart applications:

sudo cp /usr/share/applications/gnome-appearance-properties.desktop /usr/share/gdm/autostart/LoginWindow/

Log out. 
Select a new theme, wallpaper, font, icons, and pointer. 

Log in and remove gnome-appearance-properties to GDM's autostart applications:

sudo rm /usr/share/gdm/autostart/LoginWindow/gnome-appearance-properties.desktop

Simple, interactive, and no additional applications needed to make the changes.

---

