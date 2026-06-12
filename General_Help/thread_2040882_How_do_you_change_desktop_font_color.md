---
title: "How do you change desktop font color"
date: 2012-08-11
forum: General Help
---

### Post by RedRat on 2012-08-11
I am running 12.04 Gnome Classic and cannot see how to change the color of my desktop fonts. I have a light colored wallpaper image and the fonts on the icons are all white or grayish. How can I change these to black?

In my old version of 8.04, I could do this with a script file. This apparently does not work in this later version of Ubuntu. Anyone have any ideas???

---

### Post by vexorian on 2012-08-12
The gtk theme determines this.

Now, if you really like your current theme you will have to edit it. The theme might be installed in /home/youtname/.themes or /usr/share/themes Like the link says, if your theme was Ambience, then : usr/share/themes/Ambiance/gtk-3.0/apps/nautilus.css

---

### Post by RedRat on 2012-08-12
> **vasa1 said:**
> Does Gnome Classic use Nautilus? If it does, I suspect Nautilus controls the desktop appearance.
If so, you may have to edit a file related to Nautilus. I had posted on this a while ago. I'll have to search ...

See if this helps: [http://askubuntu.com/questions/89734/how-can-i-change-the-text-colour-on-my-desktop-icons/89929#89929](http://askubuntu.com/questions/89734/how-can-i-change-the-text-colour-on-my-desktop-icons/89929#89929)

It's a bit old and things change so I'm not saying this will work *now* but it did *then*.
Yes Gnome Classic uses Nautilus. I checked out the web site mentioned and it appears this might work, though I think this is rather complex to just change font colors. I guess I have a gripe with the developers who seem to have made this overly complicated for something so simple. after all, we all like different wallpapers, some dark and some light. It appears that in virtually all the themes that come with 12.04, the developers assume that everyone is using a dark wallpaper--I use them but sometimes like one that is lighter, e.g., snow scenes. 

I don't know if I want to go to all this trouble to change the font color. I guess I will chalk this up to another annoyance in the development phase of Ubuntu--I am not the first and will not be the last:)

---

### Post by RedRat on 2012-08-12
> **vexorian said:**
> The gtk theme determines this.

Now, if you really like your current theme you will have to edit it. The theme might be installed in /home/youtname/.themes or /usr/share/themes Like the link says, if your theme was Ambience, then : usr/share/themes/Ambiance/gtk-3.0/apps/nautilus.css
Is there a simpler way to edit a theme? I recall in 8.04 you could do this, but it did not have this complex file structure. See my other comments above about it being very annoying.

---

### Post by vasa1 on 2012-08-12
> **RedRat said:**
> Is there a simpler way to edit a theme? I recall in 8.04 you could do this, but it did not have this complex file structure. See my other comments above about it being very annoying.
Thanks for sharing your feelings. I'll ask the mods to delete my response since it doesn't meet your requirements.

---

### Post by vexorian on 2012-08-12
> **RedRat said:**
> Is there a simpler way to edit a theme? I recall in 8.04 you could do this, but it did not have this complex file structure. See my other comments above about it being very annoying.
Customization is something that has been going down hill lately.

I also miss that simple color dialog.


But on the brighter side, these CSS files ought be more flexible. But I really wish there was a simple GUI.

---

