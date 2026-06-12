---
title: "Very weird pointer behaviour.."
date: 2010-02-15
forum: General Help
---

### Post by rahilm on 2010-02-15
one of the mistakes i deeply regret is installing kubuntu-desktop on my ubuntu. After installation, i observed that the pointer theme had changed to the kde one, oxygen. I go to themes , customize and then pointer to find that it is actually the default theme now.,

then i go to [http://gnome-look.org/content/show.php/Chrome+Glass?content=88321](http://gnome-look.org/content/show.php/Chrome+Glass?content=88321) to install the theme. I goto themes, click install and select the package.. it says theme is successfully installed and i apply it. after i logout and login again, i find that the pointer theme has successfully changed.

When i logged in today, i found that the pointer theme was back to oxygen. What's even weird that my pointer theme keeps on changing randomly, like , when i launch firefox, It is the CG theme. When the pointer goes to the panel below, it is oxygen theme..
It is oxygen for file browser too, but the background processing icon is that of the CG theme.. 

In all, i can't seem to get a pattern in change of themes. It all appears random..
I cannot remove kubuntu-desktop as that will also remove some kde apps that i use (like kmplot, kate etc).

Plz help someone..

---

### Post by rahilm on 2010-02-18
bump..

---

### Post by chriskin on 2010-02-21
i have the same issue, even though mine is "vienna3" vs the default one ubuntu has after the installation (no kubuntu-desktop installed, meaning it probably doesn't have anything to do with it)

---

### Post by chriskin on 2010-02-22
i found it :)
you have to go to the .theme file of the theme you use, open it with gedit and write the name of the pointer where it has something about a pointer
it's a rather small file, you will undestand easily where to write it

---

### Post by rahilm on 2010-02-22
if that's the solution..then its good..too bad i can't test it..i did a full re-install of my system recently...
thnx anyway..
I'll mark this thread as SOLVED

---

### Post by chriskin on 2010-02-22
it worked for me at least and i think that there is no other reason why this bug could appear

---

### Post by rahilm on 2010-02-23
Its good there is still scope for development

---

### Post by Zorael on 2010-02-23
```
$ sudo update-alternatives --config x-cursor-theme
```
Pick the GNOME human theme.

---

### Post by darsu on 2010-02-23
I had the exact same problem with KUbuntu 9.10 - cursor theme resetting itself to Oxygen and looking different in Firefox. I ended up using the Large Mallet Approach - I 'apt-get remove'ed all cursor themes except the one I wanted to use.

---

