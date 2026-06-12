---
title: "[ubuntu/xubuntu/lubuntu] Window manager woes"
date: 2010-01-04
forum: General Help
---

### Post by Firepowerforfreedom on 2010-01-04
I seem to be plagued with a curiosity when it comes to computers. On the plus side, I never would have tried Ubuntu if it wasn't for my curiosity. On the other hand…

  I'm having a little trouble in GNOME. I was trying out some other desktop environments (XfCE, which I had used when my Apple PowerBook G3 Pismo was a Linux machine [it's happily back to Mac OS 10.4.11 Tiger now], and LXDE, which I was excited to see for the first time) on the family HP Pavilion a6400f (don't worry—it's a dual-booter with Vista and Karmic). Both desktop environments worked nicely (XfCE has changed since earlier this year, when I was using Xubuntu 9.04 rather than 9.10—and for the better), but I never can seem to leave well enough alone.
  I tried starting an Openbox session, and this ended badly (I'm used to having bars and docks and things, but the screen I got was a gray void with only a right-click on the mouse to give me a menu). After a series of restarts trying to figure out how to get back to the login screen and my beloved GNOME, I eventually found a path through by dropping to a prompt, starting X, and installing e16 (Enlightenment). From here, I was able to log out, pick GNOME, and get back into Ubuntu properly. 

  The problem? Now all my windows are missing their all-important top decoration bar (with the equally important minimize, maximize, and close buttons). In my fumblings through Openbox, I remember clicking IceWM as my window manager, and, sure enough, this looks a heck of a lot like the ever-annoying IceWM I first experienced in my experimenting with Puppy Linux (which I'd really like to get working with LXDE). 

  What's GNOME's WM anyway, and how do I get it back? I just never seem to learn. ](*,):cry:

---

### Post by cenzorrll on 2010-01-04
gnome's window manager is metacity (although i think compiz also works), you should be able to change it in a similar way to icewm.  heck you can always do:

```
sudo apt-get remove (all the packages you installed and no longer want)
```
edit: MAKE SURE IT DOESN'T DELETE SOMETHING YOU DO WANT, it'll give you a "these packages will be removed, yes/no" read through these and make sure.

then 
```
sudo apt-get install metacity
``` (you'll probably get an already installed message)

finally a:
```
sudo /etc/init.d/gdm restart
```

will restart gdm and x to get you going (other wise a full reboot may be in order)

hope that works for you!

---

### Post by Firepowerforfreedom on 2010-01-05
Thanks for all your help, but I found a way around it. Since all my files were copies of files from a Vista partition (and were still accessible), I simply deleted the home folder and started anew, copying all the files back (didn't take more than five minutes). This reset whatever setting messed up the wm.

I don't think I'll ever be so bored with Metacity again after this. Enlightenment and Openbox just can't match its no-duh interface.

---

