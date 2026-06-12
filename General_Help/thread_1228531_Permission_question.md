---
title: "Permission question"
date: 2009-08-01
forum: General Help
---

### Post by Tanatz on 2009-08-01
While viewing wallpapers, I tried to save them to the /usr/share/backgrounds folder but I am told I cannot change the contents of that folder.  Do I need to download the image through a terminal as sudo or is there a graphical way to obtain permission to save to the folder?

---

### Post by doas777 on 2009-08-01
i always download to a folder in my home (~/themes/wallpaper/) and then copy it from there, either with the terminal using sudo, or by hitting Alt + F2  and entering ```
gksu nautilus
```if you only need it for one user, I would just install it from the wallpaper screen, rather than putting it in /usr/share

I prolly wouldn't change the permissions on /usr/share/... but if you wanted to with a gui, run gksu nautilus like above, and Rclick -> Properties -> Permissions -> Other -> Write

---

### Post by mthalis on 2009-08-01
you can download files you're desktop and move/copy what ever location you want
sudo mv /home/image /usr/share/backgrounds 
sudo cp /home/image /usr/share/backgrounds

---

### Post by Katalog on 2009-08-01
You could open the terminal and issue the command

```
gksu nautilus
```

put in your password, navigate to the usr/share/backgrounds folder and save the images that way.

OR

You could just save your downloaded background images to your Pictures folder in your home directory and link to them through the Appearance Preferences from there by clicking on the "Background" tab, clicking the "Add" button and navigating to the image you want to use in your Pictures folder. That would probably the easist solution. That way you don't have to deal with the whole permissions issue.

---

### Post by Tanatz on 2009-08-01
> **Katalog said:**
> You could open the terminal and issue the command


OR

You could just save your downloaded background images to your Pictures folder in your home directory and link to them through the Appearance Preferences from there by clicking on the "Background" tab, clicking the "Add" button and navigating to the image you want to use in your Pictures folder. That would probably the easist solution. That way you don't have to deal with the whole permissions issue.

This works best, thanks for the replies!

---

