---
title: "Adding Launcher Icons to Gnome Shell Desktop"
date: 2011-10-17
forum: General Help
---

### Post by Sailejay on 2011-10-17
Hello Folks, 

With respect to Ubuntu 11.10 it's been so far so good, save a few minor issues. For example, I am having a hard time simply putting launcher icons on my desktop in GNOME Shell. I am going so far as to have to log into Unity, drag my launcher Icons (say for Firefox, or Terminal) to the desktop and log back into Shell to have the icons available on the desktop. 

I have Gnome Tweak Tool, and I can easily add the Home, Trash, or Computer icons on the desktop, but as far as simply dragging any given icon onto my desktop I'm hittin' a brick wall.

So how do I add any icon I want to the Gnome Shell Desktop without having to do so through Unity? Thanks A Ton!

---

### Post by Sailejay on 2011-10-17
I keep google searching, and am only coming up with stuff like this:

[http://www.youtube.com/watch?v=k5_q2J3XEJI](http://www.youtube.com/watch?v=k5_q2J3XEJI)


I am trying to drag Clementine's icon from the "Windows" section under "Activities" and it just opens Clementine player rather than dropping onto my desktop. Only way I can get it there is to drag and drop in Unity, then log back over to Gnome Shell.:(

Is it something simple I'm missing?

---

### Post by Sailejay on 2011-10-17
Meh, I guess not... unfortunately. Either way, if someone comes up with something please let me know.

---

### Post by kurt18947 on 2011-10-17
> **Sailejay said:**
> Meh, I guess not... unfortunately. Either way, if someone comes up with something please let me know.

 It should be fairly simple.  Once you open an app by whatever method, there should be an icon in the favorites bar (or whatever it's called.) Right-click on the icon and tick "keep in favorites". Perhaps simpler, I just do the 'super'(windows) key, search to find the application, hover over the application and right-click. One of the choices I see is 'add to favorites'. Left-click. Easy-peasy. Do either of these work for you?

---

### Post by Sailejay on 2011-10-17
> **kurt18947 said:**
> It should be fairly simple.  Once you open an app by whatever method, there should be an icon in the favorites bar (or whatever it's called.) Right-click on the icon and tick "keep in favorites". Perhaps simpler, I just do the 'super'(windows) key, search to find the application, hover over the application and right-click. One of the choices I see is 'add to favorites'. Left-click. Easy-peasy. Do either of these work for you?

Yes, I can get the app icons to that "favorites bar," but when I drag it from there to the desktop it just opens the app instead of putting it on the desktop. You try: drag an Icon, say Firefox, from your favorites bar to your desktop and see if it adds it there, or if it simply opens the app; I'm guessing it'll be the latter. 

Thanks for the response btw....

---

### Post by crdlb on 2011-10-18
GNOME Shell is not designed with desktop icons in mind. Being able to drag apps from your dash to the current workspace to launch them without leaving the overview is an intentional feature. Another example where desktop icons are ignored is how the Shell automatically opens the overview when you close the last window on a workspace.

The best workaround I can come up with is to drag applications out of /usr/share/applications in a nautilus window. You'll need to alt-drag them because nautilus is apparently unwilling to let you copy .desktop files without putting up a fight...

---

### Post by Sailejay on 2011-10-19
Thanks for the input guys. I went ahead and tried Xubuntu on a liveusb and am loving it - I'll probably do a fresh install of that tomorrow. I am not bashing Gnome Shell, I *like* it - but I feel it has a lot of evolving to do... for example, something as simple changing themes should not be so cumbersome. I see where Unity and Gnome are going, and that's all good, but for now I don't want to stand on the bleeding edge, and unfortunately I don't have the time. Gnome Shell feels like it took a lot of computing power out of my hands, then again I am a Gnome Shell noob, so whatever.

Either way thanks again, and keep plugging away at these new desktops, it's folks like you all who make it better for all of us.

---

