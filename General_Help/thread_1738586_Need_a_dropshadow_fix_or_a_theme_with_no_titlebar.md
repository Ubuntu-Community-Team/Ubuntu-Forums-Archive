---
title: "Need a dropshadow fix or a theme with no titlebar"
date: 2011-04-25
forum: General Help
---

### Post by hawthornso23 on 2011-04-25
I have made a decision to do without titlebars completely. It is a lot of vertical real estate to waste on just three buttons. I've therefore used compiz to turn off window decorations and have set up alternative methods to enable me to move/resize/maximise/minimise/close. I'm very happy with the setup I now have. But there is one problem.

Without window decorations many of my windows have no visual border whatsoever. This means when one window overlays another, for example two terminals, you cannot see where the window boundaries are at all. It is just ... whiteness. I was hopeful drop shadows could be used to do the job, but these seem to function only erratically. It works well for some windows, but not all windows seem to cast drop shadows. In particular terminal windows do not.

Does anyone know a way to add some sort of frame or visual boundary to my windows without having to get the titlebar back? One fix would be a way of getting all windows to cast dropshadows. A titlebarless theme to put a thin frame around each window would also do the job.

---

### Post by hawthornso23 on 2011-04-25
Ah - fixed it. I explicitly added gnome terminal to the list of window types casting drop shadows. For some reason gnome terminal windows don't fall into the category of `any' windows. Bizarre. But whatever - it now works.

... the trailfocus plugin to darken unfocused windows slightly also helps

---

### Post by hawthornso23 on 2011-04-25
Addendum: Google chrome windows don't cast dropshadows either. And it appears that they cannot be made to cast dropshadows even by doing the gnome terminal trick and adding them explicitly to the list. However this is bearable as at least they do have frames. 

My guess is that in order to get rid of the titlebar and put tabs up there, google chrome turns off window decorations and decorates itself. Dropshadows are collateral damage.

---

