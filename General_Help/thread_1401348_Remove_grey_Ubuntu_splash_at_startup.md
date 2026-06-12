---
title: "Remove grey Ubuntu splash at startup"
date: 2010-02-08
forum: General Help
---

### Post by rock4christ on 2010-02-08
I removed "splash" from my grub menu, but I am still getting this screen while booting:

[IMG]http://farm3.static.flickr.com/2741/4065116844_1679136325.jpg[/IMG]

Is there a way to remove it?

---

### Post by running_rabbit07 on 2010-02-08
I know the feeling, I get the UBUNTUSTUDIO splash, then a few seconds of that karmic splash. I do admit that I like the Koala's splash.

---

### Post by ElSlunko on 2010-02-08
Not the exact solution you're looking for but it may help :

[http://gnome-look.org/content/show.php/XSplash+Background+Settings?content=114984](http://gnome-look.org/content/show.php/XSplash+Background+Settings?content=114984)

---

### Post by n0dix on 2010-02-08
See this post: [http://ubuntuforums.org/showpost.php?p=1726890&postcount=2](http://ubuntuforums.org/showpost.php?p=1726890&postcount=2)

---

### Post by rock4christ on 2010-02-08
> **n0dix said:**
> See this post: [http://ubuntuforums.org/showpost.php?p=1726890&postcount=2](http://ubuntuforums.org/showpost.php?p=1726890&postcount=2)

that option was already unchecked

---

### Post by n0dix on 2010-02-08
If you want remove the splash because is very ugly you can try install Slim. If very simple, and more lightweight than gdm.

---

### Post by rock4christ on 2010-02-08
> **n0dix said:**
> If you want remove the splash because is very ugly you can try install Slim. If very simple, and more lightweight than gdm.

what is slim? also, im wanting to remove it to speed up boot(every ms counts)

---

### Post by rock4christ on 2010-02-08
bump

---

### Post by n0dix on 2010-02-08
> **rock4christ said:**
> bump

Try with the 6th post: [http://ubuntuforums.org/showthread.php?t=1305659]("http://ubuntuforums.org/showthread.php?t=1305659")

---

### Post by rock4christ on 2010-02-08
that completely stops gdm. I just want to remove the ubuntu logo thing that i posted above.

---

### Post by Uncle Spellbinder on 2010-02-08
You can change it to whatever you want with GDM2 Configuration Tool. It changes the image from the brown background to anything you want. See link in my sig for the PPA repo.

---

### Post by rock4christ on 2010-02-08
can't get the public key. when I try to add it keyserver.ubuntu.com times out

---

### Post by Uncle Spellbinder on 2010-02-08
> **rock4christ said:**
> can't get the public key. when I try to add it keyserver.ubuntu.com times out
Server is probably a bit busy. Wait and try later.

---

### Post by rock4christ on 2010-02-08
Is there a way to disable gdm for logon only(so that logon is no gui, but then gome loads up my desktop)? or, just a way to make that completely disappear, as I autologin.

---

### Post by n0dix on 2010-02-08
Auto login: [http://www.killertechtips.com/2008/04/09/how-to-auto-login-to-ubuntu/](http://www.killertechtips.com/2008/04/09/how-to-auto-login-to-ubuntu/)

---

### Post by rock4christ on 2010-02-11
I already autologin

---

### Post by rock4christ on 2010-02-12
I found a solution:

remove xsplash with 
mv /etc/gdm/PreSession/Default /etc/gdm/PreSession/Default.disabled

---

