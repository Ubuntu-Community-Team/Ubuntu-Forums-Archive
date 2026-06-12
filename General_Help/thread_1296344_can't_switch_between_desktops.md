---
title: "can't switch between desktops"
date: 2009-10-20
forum: General Help
---

### Post by dandaowolf on 2009-10-20
I am new to Linux, running Ubuntu 9.04, and cannot figure out how to switch desktops.  I am on Desktop 2 right now, which no longer has any panels.  I would like to know how to switch between desktops and/or how to get back my panels.

A second, possibly related issue:  Desk1 is wallpapered by whatever the default is.  Desk2 is wallpapered through compiz so that I have different wallpapers on each workstation.  I have not yet tried 3 desktops so do not know what Desk3 would look like.

I would like to have Desk1 to be wallpapered by compiz so I can make each workstation a different wallpaper.

---

### Post by oldos2er on 2009-10-20
Ctrl-Alt+left arrow or right arrow.

---

### Post by mick222 on 2009-10-20
To switch desktops there should be some small squares bottom right on the taskbar just click.Or use ctrl + alt and the arrow keys. If the workspace switcher is missing just right click on bottom panel choose add to panel and enable workspace switcher.

---

### Post by dandaowolf on 2009-10-20
Ctrl + Alt + arrow changes workstations.  I want to change Desktops.


I have no visible panels/taskbars.  Thus I cannot add a desktop switcher to them.

---

### Post by mick222 on 2009-10-20
> A second, possibly related issue: Desk1 is wallpapered by whatever the default is. Desk2 is wallpapered through compiz so that I have different wallpapers on each workstation. I have not yet tried 3 desktops so do not know what Desk3 would look like.

I would like to have Desk1 to be wallpapered by compiz so I can make each workstation a different wallpaper.
 
 Normally the same wallpaper is on all desktops if you want to change this you need to install compizconfig settings manager (search ccsm in synaptic)
 Check this article 
[http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/](http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/)
it gives easy tro understand instructions.

---

### Post by mick222 on 2009-10-20
you should have a panel at the top with the time date etc .
and one at the bottom with workspace switcher and showdesktop.

---

### Post by mick222 on 2009-10-20
Sorry just realised skipped the bit about missing panels this is probably a compiz issue used to get it in fiesty ubuntu 7.04 disable compiz and logout login the panels should reappear ctrl+alt +arrow does change workspace. Workspace and desktop are same thing.Are you sure you didn't delete them by mistake because this is the first time since then i've heard of panels just vanishing.

---

### Post by dandaowolf on 2009-10-20
> **mick222 said:**
> Sorry just realised skipped the bit about missing panels this is probably a compiz issue used to get it in fiesty ubuntu 7.04 disable compiz and logout login the panels should reappear ctrl+alt +arrow does change workspace. Workspace and desktop are same thing.

Will try once I figure out how to log out without any panels.  

As to the workspace/desktop thing, I was under the impression that they are two similar but separate things.  On my system I have two cubes (I thought desktops), each with 4 faces (I thought workspaces).

The first cube's faces are all wallpapered the same, and I believe all still have top and bottom panels.  The second cube (the one I am on now) has different wallpapers for each face and has no panels now (although it did in the past).

---

### Post by mick222 on 2009-10-20
did you do any updates before this happened

---

### Post by mick222 on 2009-10-20
press alt +f1 should start desktop menu bar

---

### Post by oldos2er on 2009-10-20
> **dandaowolf said:**
> Will try once I figure out how to log out without any panels.  


 Alt-F2, type in gnome-terminal, type in logout.

 Edit: on second thought, this will most likely not work without a panel running. Sorry.

---

### Post by dandaowolf on 2009-10-20
no updates right before this happened.  

When I followed the instructions here  [http://anuragbansal.wordpress.com/20...ace-in-ubuntu/]("http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/") I was able to log out and back and have panels again but things are still a little borked.[ ]("http://anuragbansal.wordpress.com/2008/05/10/how-to-get-different-wallpapers-on-each-workspace-in-ubuntu/")

I tried to follow similar instructions somewhere else and I think that might be my problem.  I think that I have multiple programs (nautilus, etc.) that are all trying to paint my desktop and are just confusing each other and me.

Thanks for the help, I think I am at least to a point where even if I do not understand things, I can get back to some place with panels where I can then run programs, logout, etc.

---

### Post by mick222 on 2009-10-20
firstly i'd simplify things by clicking the workspace shifter and change it to 4 colums 1 row this will give you 4 desktops .

---

### Post by dandaowolf on 2009-10-20
> **mick222 said:**
> firstly i'd simplify things by clicking the workspace shifter and change it to 4 colums 1 row this will give you 4 desktops .

so what this does for me is give me 4 sets of cubes (16 desktops).  Each cube has 4 different wallpapers.  If I Ctrl+Alt+arrow it switches between the different wallpapers.

If I click on another desktop on the workspace shifter, it places me on the same side of the next cube-- i.e. if my 4 wallpapers of the cube are red, green, blue, and black, respectively, clicking on the switcher of red side of cube1 places me on the red side of another cube.  Pressing Ctrl+Alt+arrow switches between the red, green, blue, and black sides.

---

### Post by mick222 on 2009-10-21
no it gives you just 4 workspaces on 1 line I think you have 2 instances of workspace switcher on the panel showing the same workspaces or desktops what ever you want to call them.You cant have more than one cube it is the same cube.

---

