---
title: "Mouse Flashes In and Out"
date: 2011-08-17
forum: General Help
---

### Post by brammoran on 2011-08-17
Hi all!

Well, I have a strange problem that I can't really seem to find a fix for. My mouse flickers in and out when I move it and a small pix elated square surrounds it. I can still click and highlight and preform mouse actions.
I was playing about in the Appearance settings and I had come over to the mouse pad of the custom theme window. I tried changing the mouse and it only changed some icons of the mouse. To make it work and show all the new icons for the cursor, i used this command:

```
sudo gedit /usr/share/icons/default/index.theme
```

I then changed "Inherits=DMZ-White" to "Inherits=DMZ-Black". I logged out and back in and that's when my problem started. It shows the new mouse but i have that glitchy square and it flickers. I've tried switching back but it didn't change anything. Please help if you can!

---

### Post by brammoran on 2011-08-17
Hey, I managed to fix it with this:

[http://www.giannistsakiris.com/index.php/2007/12/20/ubuntu-mouse-pointer-is-randomly-disappearing/](http://www.giannistsakiris.com/index.php/2007/12/20/ubuntu-mouse-pointer-is-randomly-disappearing/)

---

