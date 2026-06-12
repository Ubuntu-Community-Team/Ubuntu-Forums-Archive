---
title: "Disappearing windows"
date: 2012-04-22
forum: General Help
---

### Post by runner87 on 2012-04-22
Hi everyone

So up until a day or two ago everything was fine on my computer. I am running Ubuntu 11.10. Now all of the sudden, whenever I try and open certain windows, they seem to flash up and disappear suddenly. Some specific windows that I have noticed this problem with: sound preferences(from system settings), file properties(in nautilus), and the update manager. I've never seen this happen before and can't seem to trace it back to any specific problem. This is happening in both Unity and Gnome, and i've tried resetting all my gconf settings. If anyone has had this happen to them before I'd love to hear from you. Thanks everyone for reading.

---

### Post by GameX2 on 2012-04-22
Hi,

You mean you can't access your programs that dissappear, or your windows dissappear from the screen?

If they do, are they simply on another workspace?
That happen to me sometimes.

Good luck;

---

### Post by runner87 on 2012-04-22
Thanks for the quick response!

To be more specific, the program seems to shut down entirely with no error message whenever this happens. For example, whenever I right click on a file in nautilus and select "properties", the properties window briefly appears, then the entire program crashes. My desktop icons also vanish, which I assume is because they are controlled by nautilus. 

This problem is not specific to nautilus, this happens with many preferences and settings windows.

---

### Post by GameX2 on 2012-04-22
Uh, that suck! :(

Never heard about that, sorry. ;(
About the desktop icons, they are controlled by Nautilus, as well; when Nautilus close, the Desktop disapear (Just like Explorer.exe in Windows, when you close it).

Does this happen on softwares as well, Blender, Gedit..?  Or only GNOME windows, like the settings?  If softwares doesn't crash, but GNOME settings does, I assume this is a problem with GNOME?

---

### Post by runner87 on 2012-04-22
That's the weirdest thing, some other gnome setting windows work just fine, like the window appearance preferences. But the keyboard preferences crashes. I wish I had something more to give you guys to go on.

I did notice that when nautilus crashes, it's a segmentation fault that's responsible, so it would seem that it's more than just a wrong setting that's causing it.

---

### Post by tmaranets on 2012-04-22
Which programs do you have in which the application windows disappear? I am guessing this is a Gnome error. If you can access a browser in Ubuntu without the windows closing, try installing Gnome again to see if anything changes.

---

### Post by runner87 on 2012-04-22
OK so this seems to be getting into a deeper problem with my setup.

So i uninstalled GNOME and GNOME shell. Now when I try to reinstall it I get this nasty thing:


The following packages have unmet dependencies:
 gnome : Depends: gnome-core (= 1:3.0+1ubuntu1) but it is not going to be installed
         Depends: cheese (>= 3.0) but it is not going to be installed
         Depends: gnome-games (>= 1:3.0) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

I can't seem to install the dependencies

The original error is still occurring

---

### Post by runner87 on 2012-04-22
OK great news guys - I fixed it.

I can't say I pinpointed the exact problem, but I played around a lot with synaptic and uninstalled just about every package that had anything to do with ubuntu and gnome. Then i upgraded through Synaptic -> Mark all upgrades. Restarted, and reinstalled ubuntu-desktop and unity. And ta-da! everything is fixed. Except, of course, for what I broke to fix it. 

Thanks for all the help, a great first adventure into the forums. Now i need to figure out how to fix held broken packages, whatever they are.

---

### Post by GameX2 on 2012-04-22
Hey, nice job!
Glad it worked! ;)

I know how you feel frustrated when something goes wrong on Ubuntu! I just fixed my super-slow wifi connection! :D
Well, in my case, why I get frustrated when I have these problems, the reason is simple: I now love Ubuntu so much that I CAN'T get back to Windows... ;)

(Well, I could, but I almost never use it.  I paid for this? XP)

---

