---
title: "Hiding gnome apps"
date: 2006-03-26
forum: General Help
---

### Post by ubuntukid on 2006-03-26
I just installed kubuntu-desktop on my ubuntu install and I have to say that I think kubuntu is much nicer. The only problem I have right now is that my menu is cluttered with gnome applications from ubuntu and I was wondering how I can hide them. I heard that it was possible without actually uninstalling ubuntu.

I may get rid of ubuntu and only use kubuntu but I don`t want to make that move just yet.

---

### Post by magnusbb on 2006-03-26
Have a look at this:
[http://www.kde-look.org/content/show.php?content=31031](http://www.kde-look.org/content/show.php?content=31031)

What it does is that it puts all the GNOME applications it can find, inside its own "GNOME" folder in the K Menu. Now the GNOME applications won't mix with your KDE applications - but you're still able to use them! Smart.

---

### Post by ubuntukid on 2006-03-26
I`m having trouble installing this. When I make the deb file executable I get an error message. "/home/aleks/Desktop/31031-kmenu-gnome_0.4-1_all.deb" and that`s it. What`s wrong?

---

### Post by lupine_nickt on 2006-03-26
Making it executable?

You don't need to do that - the .deb is a package (like the ones you install through adept or synaptic), so you want to install it. It's not in apt-get, so you need to use dpkg:

in the terminal, type "sudo dpkg -i /home/aleks/Desktop/31031-kmenu-gnome_0.4-1_all.deb"

That should do the trick. I don't have GNOME installed, so I'm a bit leery to try it...

xF,

....Nick

---

