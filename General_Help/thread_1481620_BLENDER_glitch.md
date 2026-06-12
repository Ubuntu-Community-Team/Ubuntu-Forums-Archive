---
title: "BLENDER glitch"
date: 2010-05-12
forum: General Help
---

### Post by dzwestwindsor on 2010-05-12
hey

i installed blender, and the top tool bar doesn't work. (file, add, timeline, etc)

I roll over, they sense me rolling over, but click on it doesn't work

everything else in blender seems to be running fine

Runing 10.04, same prob with 9.10

---

### Post by dzwestwindsor on 2010-05-13
no one has experienced this problem before???

---

### Post by joebu23 on 2010-05-13
Some questions:

Are you running Gnome? KDE? Other?

Have you tried going into System -> Synaptic and completely removing Blender, rebooting, and re-installing?

Since installing have you tried to reboot? (The mouse might not be connected is a theory) Are you sure your mouse works?

---

### Post by jacob_ewing on 2010-05-30
I'm having much the same issue.  I use(d) Blender regularly without  problems, but after switching from Ubuntu 9.10 to 10.05, I have this  problem.

The catch here is that I also installed it on a new PC, so it might be a  hardware issue. I'm definitely using a different video card.  I used to  use an "MSI FX5200-TD128LF" card (Translation: that's the number I see  when pulling it out of the old motherboard, I don't know much else about  it), and am now using an on-board controller.

If I do "lspci" from a shell, I get this line:

01:05.0 VGA compatible controller: ATI Technologies Inc RS880 [Radeon HD  4200]

Which, if I plug the controller name into Google, I get many many hits  of bug reports on various GNU/Linux distros.

Symptom-wise, I'm seeing much the same thing:

If I run Blender in "windowed" mode, the menus are... wonky ...  If I  click on the menu, nothing appears to happen.  If I then move the mouse  down to where the submenu would show up, it appears in the appropriate  place. Similar behavior happens when I hit the space bar to get the  editing menus.  It's almost as if Blender is updating things properly in  it's own world, but a step behind on talking to the display.

Interestingly enough, when I run it in full-screen mode, it works very  smoothly, with two exceptions:
1) My desktop is set up to auto-flip when the mouse hits the edge of the  screen.  It's in a 2x2 layout.  When I flip vertically, I get my normal  desktop.  When I flip horizontally, I see a messed up version of the  Blender screen.  Flipping back to the ~actual~ Blender screen sometimes  gives me a mildly messed up one, and sometimes gives me a proper one.
2) It only worked smoothly until I hit F12 to render the image.  It  rendered nicely, but when I closed the display window, the whole screen  was messed up quite badly (on all four desktop areas).  I actually had  to reboot in order to recover the screen.

Interestingly enough, when I rebooted and started Blender again, I could  see the same objects that I created previously - again with the screen  slightly messed up.  They weren't actually there in the editor (never  got saved :-( ) but the image of them was displayed.

In my case, this is running on a GNOME desktop, and  uninstalling/reinstalling has happened twice.  I haven't yet tried  installing it from a tarball, but I'm thinking this is a hardware issue  anyway.

Sorry 'bout the excessive verbosity.

---

### Post by vahtenberg on 2010-07-28
Have the same card (free drivers) and the same problems as **jacob_ewing**. But fullscreen doesn't help me :(


**Update:** i've just booted gentoo and tested blender there - everything works with free drivers and blender-2.49a. 
So it seems to be a problem of ubuntu's blender package. I'll try to build it myself.
De bene esse i'm running Ubuntu 10.04 Lucid Lynx (fresh install). All packages are up to date.

**Update:** Found temporary solution [here](http://ubuntuforums.org/showthread.php?t=1319407):
```

LIBGL_ALWAYS_SOFTWARE=1 blender

```

---

