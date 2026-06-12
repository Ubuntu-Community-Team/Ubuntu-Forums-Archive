---
title: "Changing Themes/Login Screen"
date: 2009-10-30
forum: General Help
---

### Post by xjb2003x on 2009-10-30
I have been wondering around the forums searching for a way to do this.  I did a fresh install of 9.10 last evening.  The new login screen just doesn't do it for me.  So, I went to gnome-look.org in hopes of finding a replacement.  I found a few to my liking.  Before I would open a terminal and type gdmsetup, window would pop up and I would change things from there.  

In 9.10, this does not come up.  I tried to manually move the theme files to /usr/share/gdm/themes/<mytheme>, that failed to work as well.  I tried to install it through the appearance menu to no avail.  Is this possible to do with the new version?  Any help/direction would be greatly appreciated!

---

### Post by hambone79 on 2009-10-30
I am having a similar issue. I have a custom GDM theme that has my company logo that I would like to use in place of the hideous default theme in Karmic.

---

### Post by dummy910 on 2009-10-30
```
sudo apt-get install startupmanager
```
then look for an icon-program in System>Administration>Startup Manager or type:
```
su-to-root -X -c /usr/sbin/startupmanager
```
to launch via a terminal.

---

### Post by xjb2003x on 2009-10-30
Thanks for your help.  I got the startup manager installed, however, the various themes I've downloaded from gnome-look.org do not seem to work.  

Has anyone got this to work successfully?

---

### Post by Good_Newz on 2009-10-30
Read this [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

---

### Post by hambone79 on 2009-10-31
> **Good_Newz said:**
> Read this [http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html)

This is the first thing I tried and it doesn't work.

---

### Post by Good_Newz on 2009-11-03
This might help [http://ubuntuforums.org/showpost.php?p=7576112&postcount=365](http://ubuntuforums.org/showpost.php?p=7576112&postcount=365)

---

### Post by tacantara on 2009-11-03
I've been trying to download window themes, etc., using the link provided in the themes GUI.  When I click on a window dressing I like, the page refuses to load and eventually times out.  Has anyone else found this to be true?

---

### Post by ranch hand on 2009-11-03
The login box itself is tough to change.  The background image is not.  The GDM gets its image the same place xsplash does /usr/share/images/xsplash.  You have gimp.  The size and resolution needs to be the same on all of the images as the ones in there.

---

