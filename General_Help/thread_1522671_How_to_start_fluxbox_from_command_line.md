---
title: "How to start fluxbox from command line ?"
date: 2010-07-02
forum: General Help
---

### Post by uncle-c on 2010-07-02
I have both gnome and fluxbox install. Usually when I start the computer I get presented with GDM and then  I can choose which WM I can use. However, I don't want to go into GDM and want to run my X sessions from command line. I can run gnome by using the **startx** command from the prompt. But how do I fire up fluxbox ? When I run the fluxbox command I get "Could not connect to  Xserver" errors.
The only way I can run flux is to edit my .xinitrc file,  replacing 
```
 exec gnome-session 
```

with

```
 exec fluxbox
```

and then running **startx.** There must be an easier way of doing this.

thanks

---

