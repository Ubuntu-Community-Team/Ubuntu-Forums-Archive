---
title: "How can I add new wallpapers for all users? (10.04)"
date: 2010-08-12
forum: General Help
---

### Post by redvenomweb on 2010-08-12
I see that the default wallpapers seem to be in /usr/share/backgrounds and while I can add more images to this directory, they don't show up in the list when I go to the Change Desktop Background dialog.

I can manually add them in that dialog (via the Add) button, but that won't propagate to the other users, which is my goal.  How can I do this?  (edit: I would also like to ensure that this propagates to future new users, as well.)

---

### Post by pbrane on 2010-08-12
you need to add the backgrounds to */usr/share/gnome-background-properties/ubuntu-wallpapers.xml*. Those files will show up in the background preferences dialog. And they should be visible to all users.

---

### Post by redvenomweb on 2010-08-12
Thanks, that set me on the right path.

What I did was copy all the images to /usr/share/backgrounds, added them to my Wallpaper list using the Add dialog, then found *~/.gnome2/backgrounds.xml* and copied that over */usr/share/gnome-background-properties/ubuntu-wallpapers.xml* (as opposed to adding my images one-by-one to that file).

I'll report back if there's any problem with this solution.

---

### Post by WorMzy on 2010-08-12
Since your question has been answered, I'll just point out that you'll need to store the wallpapers in a location that all users can read, so if you've used images from your home area, you may need to move them to /usr/share/backgrounds and edit the XML entry accordingly.

---

