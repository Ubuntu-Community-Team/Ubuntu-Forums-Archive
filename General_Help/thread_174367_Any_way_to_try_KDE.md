---
title: "Any way to try KDE???"
date: 2006-05-11
forum: General Help
---

### Post by morbid_bean on 2006-05-11
Is there anyway to try out kde when I already have gnome?....if so..is it a package...and if it is whats it called....or a download??? And if i do this will i have a chance at data loss??? and will i be able to uninstall it if i dont like it??

---

### Post by Sef on 2006-05-11
> And if i do this will i have a chance at data loss???

Always a chance, but not high with this.  But **back up**your data first.

> .if so..is it a package...and if it is whats it called....or a download???

There are two ways to it:

1) If you have enough room on your hard drive, simply dual boot with Ubuntu and Kubuntu.

2) Type these commands from the terminal (Applications > Accessories > Terminal)

sudo apt-get update

sudo aptitude install kubuntu-desktop

> and will i be able to uninstall it if i dont like it??

Use aptitude instead of apt-get.  Makes uninstalling much easier.

You will see Kubuntu icons on Ubuntu and vice-versa.

---

### Post by s_h_a_d_o_w_s on 2006-05-11
Once you install it, what is the command to uninstall it?

---

### Post by morbid_bean on 2006-05-11
imma do the second way...now if i do uninstall it...will it also take all of the kde packages out for me or will i have to manualy do that?

---

### Post by morbid_bean on 2006-05-11
yea and whats the code? for uninstalling it???

---

### Post by aysiu on 2006-05-11
If you install it with *aptitude*, you use this command: ```
sudo aptitude remove kubuntu-desktop
```

I would do a ```
sudo aptitude update
``` before the ```
sudo aptitude install kubuntu-desktop
``` just to be on the safe side.

If you install it through apt-get or Synaptic, you will have manually remove all the dependencies.

---

### Post by sinkxdie on 2006-05-11
sudo aptitude remove kubuntu-desktop
                                    or
sudo aptitude uninstall kubuntu-desktop

im unfimilar with aptitude

---

### Post by purdy hate machine on 2006-05-12
If you just want to try KDE and have a decent internet speed why not download one of the live KDE based distro’s? Then you can safely explore it before you take the plunge and make changes to your pc.

---

