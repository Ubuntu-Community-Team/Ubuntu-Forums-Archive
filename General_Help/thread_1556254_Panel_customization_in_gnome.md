---
title: "Panel customization in gnome?"
date: 2010-08-19
forum: General Help
---

### Post by Manuwash on 2010-08-19
Hi

I have ubuntu 10.4 with compiz fusion and emerald themer, and I would like to know if there's any good way to download themes not only for the window decorations but also for the panels. I use cairo dock opengl on the bottom but I do use the top panel and I would like to be able to download some cool themes for it and not just the limited customization found on the panel properties

thanks

---

### Post by mcduck on 2010-08-19
The panel "themes" are just pictures. You can use at least JPG, PNG, XPM and SVG images, and simply drag&drop one into some empty spot in the panel to set it as your panel background (or set it from the panel's preferences).

For best results make the image the same size your panel is. If you need to, you can enable scaling/rotating of the panel background image through gconf-editor.

Apart from the backround the Gnome-panel simply uses the same GTK theme all your other applications are using.

---

### Post by Manuwash on 2010-08-19
cool, so what about making the sub menus match instead of just being a boring plain white?

---

### Post by mcduck on 2010-08-19
> **Manuwash said:**
> cool, so what about making the sub menus match instead of just being a boring plain white?

That comes from the GTK theme you use. But at least it sure is possible, you just need to get a GTK theme that does that...

Unless you manage to find a theme you like from [http://gnome-look.org/]("http://gnome-look.org/") you'd pretty much just have to learn how to make your own GTK theme. Which isn't *that* hard if you have no problems with hand-editing text files, especially if you use some theme that's close to what you want as a starting point and then start changing it to your liking. But it will definitely take a bit of work and time to figure out.

There *is* a graphical tool that is able to edit GTK themes to some level (Gnome-color-chooser), but I don't know if it's able to change the panel menu colors separately from other menus. You could of course install it to see if it can do what you want.

---

### Post by fabounet on 2010-08-20
what about using Cairo-Dock for the top panel too ?
it's possible with the latest 2.2 version, see [this demo]("http://www.youtube.com/watch?v=voco3Kj1Fxo")
it would also save you from running a gnome-panel.

---

### Post by Manuwash on 2010-08-21
haha I just posted a message on the youtube demo asking that, because I believe it's a great idea just perfect for people who want something better looking than the panels, and what better than cairo dock? 

So how you get the top dock as the demo video? what about making a theme which comes with that already setted up? it would be a cool idea. Just mimic the standard top panel that comes with ubuntu but with the dock. I am interested :)

---

### Post by drdanielfc on 2010-08-21
gnome-color-chooser ;)

---

### Post by fabounet on 2010-08-23
> what about making a theme which comes with that already setted up?
it's already available (theme "Unity-1")  :-)
the view used for the top dock is the "Panel" one, and the "3D plane" for the bottom dock.

---

### Post by Manuwash on 2010-08-25
Just wanted to let you all know that I am using the unity 1 theme and it works like a charm, thanks fabounet, great job!

---

### Post by fabounet on 2010-08-26
thanks for the feedback :-)

---

