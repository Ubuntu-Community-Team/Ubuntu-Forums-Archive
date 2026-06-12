---
title: "Small change to icon theme"
date: 2006-04-16
forum: General Help
---

### Post by ncappel1 on 2006-04-16
how does one go about modifying the default icon theme to only change one or two icons? 

i've been fishing around in /usr/share/icons/gnome(the default theme I use)/48x48/mimetypes and replacing the icons I want to use with new ones. 

Example, copy the name of the default .png into the name of the one I want to use, then replacing the new with the old. This method hasn't been working.

I am specifically trying to change the icons of media files, like ogg and mp3

Am I doing the right thing?

---

### Post by hegenious on 2006-04-17
right click the file or program who's icon you want to change, choose 'properties'.
In the properties sheet click the default icon, the icon chooser opens.
It has a 'browse' button on top right of the window, hit that and a little file browser opens. Now if you for instance would like to change the ugly firefox icon for the one that is in say the gartoon icon themes, browse to: 

/home/**your-name**/.cons/**gartoon**/scalable/apps/

Hit 'open' and all the gartoon icons are now displayed! Choose one you'd like for your file or program and you are all set.  :cool: 

[replace the bold parts in the path with your own]  **bye**

---

### Post by z_diver on 2006-04-17
[QUOTE=ncappel1]how does one go about modifying the default icon theme to only change one or two icons? 

i've been fishing around in /usr/share/icons/gnome(the default theme I use)/48x48/mimetypes and replacing the icons I want to use with new ones. 

Example, copy the name of the default .png into the name of the one I want to use, then replacing the new with the old. This method hasn't been working.

I am specifically trying to change the icons of media files, like ogg and mp3

Am I doing the right thing?[/QUOTE]
You can certainly do what you are doing.  I'd make a copy of that particular directory and then open the index.theme file(inside) and change the name field from GNOME to whatever you named the copy of the folder.  Then go to town and change your icon theme to the new one.  The reason I'd do it this way is because if Ubuntu decides to update the gnome-desktop packages your custom artwork could be overwritten.

---

### Post by ncappel1 on 2006-04-17
Ok I figured out what I was doing wrong. The answer dawned on me when Ibooted up this morning and everything was working just the way it should have. 

When I was making the changes in the folder in order to see them you have to restart x. This makes sense to me now, as the default icons are loaded once at the login of each user. Any changes made won't show up uptil you log in again and reload all that information.  

thank you to everyone. talk about a lucky/**intuitive** answer! ;)

---

